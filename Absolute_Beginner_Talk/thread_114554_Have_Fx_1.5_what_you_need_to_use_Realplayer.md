---
title: "Have Fx 1.5? what you need to use Realplayer"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by nu2this on 2006-01-08
If you're new to Ubuntu (as I am) & if you have used Realplayer to view videos in Fx, such as the BBC video news service, then please let me save you the journey I took
1) get realplayer this way it's the easiest
A. ```
 sudo gedit /etc/apt/sources.list 
```
B. add this to your sources.list
## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
C. then:  ```
sudo apt-get update
sudo apt-get install realplay
```
2) After You've done that go to firefox extensions & get MediaPlayerConnectivity0.4.9.4
3) After you've installed it'll go thru an install wizard use th drop down menu for on its 2nd page select reaplayer for audio & video click thru the rest of the install wizard. After that instead of the mplayer you'll see the MPC logo click it & it'll start playing videos in realplayer in Fx1.5!
At least it did for me.
thanks to Artificial Intelligence & frodon for their posts which helped immensly.\\:D/

---

