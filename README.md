# AI Journey 2020 "Digital Peter: recognition of Peter the Great's manuscripts" 
Basically the solution was pretty classic, I used LSTM+CTC loss on top of Effnet feature extractor. The main problem was GPU memory limitation so I coulnd't fully use complex effnet versions with normal resolution. As I workaround I was using gradient accumulation but it didn't improve the score much. I assumed that it was because BS was too small for batch normalization to work well. So I first trained network with batch size=16 and relatively low-resolution images. Then I freezed BN layers, reduced batch size, upscaled images and trained network with gradient accumulation. At the end I just used a voting ensemble of models trained such way. This approach gave me the best result.
### Final results:
![](https://sun9-2.userapi.com/impg/RTbi5YvVh2BxlpmpjP_VyFpEdn1IBGQvT83gxQ/jbLuLwc4Rak.jpg?size=982x625&quality=96&proxy=1&sign=24633a9f75db48ae45b55db49a824a9a)
