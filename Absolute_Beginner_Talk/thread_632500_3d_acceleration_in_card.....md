---
title: "3d acceleration in card...."
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by nikoPSK on 2007-12-05
I have an nvidia GeForce 5200 GTX and I installed the restricted driver. In peggle under wine it says My card isn't powerful enough. I read somewhere that i need to install nvidia-glx and some nvidia settings manager. i would be happy if someone could point me through this.

Niko

---

### Post by reckless2k2 on 2007-12-05
well i think this is a wine issue that you can't get around. i don't think it has anything to do with the nvidia driver install. do you have compiz and all affects running fine?

---

### Post by forestpixie on 2007-12-05
if you've installed the restricted driver I think that will be what you need, whether thats enough is a completely different question :)

check in synaptic as to what nvidia driver you have installed and if you've got the nvidia settings manager you can get it from terminal

```
nvidia-settings
```

i you want to change anything in ther ethough you'll need to gksudo it

---

### Post by skjoldfetter on 2007-12-05
wine is a program used to run windows programs.. has nothing to do with his graphics card...

i had similiar problems... try entering
 ```
sudo nvidia-settings
```

in a terminal and see if a window comes up

---

