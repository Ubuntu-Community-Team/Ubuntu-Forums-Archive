---
title: "Problems watching movies"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by boyturtle on 2007-04-24
Newb to Linux. Have installed Ubuntu 7.04. Have several 'teething' problems, the main one is not being able to watch movies through Movie Player (mpeg, mpg, wmv, asf) although I can hear the sound fine.  If I switch between workspaces, i sometimes (but not always) get the picture on my return to the original workspace were Move Player was running, but it mysteriously disappears as soon as I touch (any part of) the player

I have a Radeon 9550 with 256 mb and am running the original drivers that loaded with the install

Any ideas anyone?:confused:

---

### Post by supersonicdarky on 2007-04-24
try playing it in vlc, it plays almost anything

---

### Post by taurus on 2007-04-24
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by boyturtle on 2007-04-24
Sadly that did not work,  any other ideas?

---

### Post by marko_4454 on 2007-04-24
> **boyturtle said:**
> Sadly that did not work,  any other ideas?

Have you tried this in terminal:
```
sudo apt-get install libdvdcss2
```

---

### Post by drascus on 2007-04-24
Hey boyturtle, 
 I agree with supersonic. Go to synaptic and download VLC Media player. Then I suggest going to firefox extensions and downloading the mediaconnectivity. that program will allow you very easily to view embeded internet media in any application you choose it makes surfing easier. good luck.

---

### Post by boyturtle on 2007-04-24
no, that didnt work either. same problems occured

---

### Post by boyturtle on 2007-04-25
> **marko_4454 said:**
> Have you tried this in terminal:
```
sudo apt-get install libdvdcss2
```

Once i did this and did all the automated update following a reboot, it seems to have sorted it all out.... 

Thanks alot

---

