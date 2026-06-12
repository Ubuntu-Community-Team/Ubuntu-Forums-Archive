---
title: "Drives and Wallpaper suddenly gone"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by jpr13 on 2008-01-23
I just booted Gusty twice and my wallpapers are gone and my two drives are gone. 
I had a data drive and my windows xp partition mounted on my desktop.
This is easy to fix, but how can i keep this from happening again.
I was using vmware and a win98 guest, but could that damage anything?

                                              Jason

---

### Post by smacattack on 2008-01-24
Did you try 

```
sudo gedit /etc/fstab
```  ??

same thing happened to me a couple of days ago and I went in there and unchecked a couple of lines and it all works fine now. I use VMWare as well so I don't know if that was what caused my problem too but... I think it was when I booted into my old XP partition and then back out again but I'm not sure...

anyways maybe try looking in there... sorry if it doesn't help.

---

