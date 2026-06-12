---
title: "Updated drivers in windows, resolution goes haywire"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Nevon on 2007-12-09
I just updated my video drivers in Windows (I'm dual booting) and everything was fine. Then I boot into Ubuntu, and find that I'm stuck using 640x480 at highest. Normally I'm using 1280x1024 just fine, but for some reason I couldn't. After some googling I try to edit my xorg.conf-file, but from what I could tell, lots of different resolutions should be available to me.
After some more googling I find that someone had a similar problem as me, but solved it by selecting the Nv drivers, instead of the NVIDIA drivers. So I did the same, and now it's working properly again. 

But why did this happen in the first place? 
I'm using an Nvidia Geforce 7300GS video card.

---

### Post by Delvien on 2007-12-09
Check out System>Administration>Screens and Graphics.

You have to kind of play around with that till you find the right options, unfortunately its a weird bug ( i think) and I had to deal with this recently too. Its something to do with either Xorg or bulletproof X borking things up.

---

### Post by SOULRiDER on 2007-12-09
Using the nv drivers isnt really what you can call cool, since you wont have 3D acceleration. why dont you try to reconfigure your Xorg? You can do that by typing this ina  terminal:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Nevon on 2007-12-09
> **SOULRiDER said:**
> Using the nv drivers isnt really what you can call cool, since you wont have 3D acceleration. why dont you try to reconfigure your Xorg? You can do that by typing this ina  terminal:
```
sudo dpkg-reconfigure xserver-xorg
```

3D acceleration using the NV drivers worked for me. I could still play games, use compiz-fusion, and AWN. However, I did as you said, and now the Nvidia drivers work with my resolution. 
But again, why did this happen? Why does it make any difference what drivers I'm using in WINDOWS?

---

