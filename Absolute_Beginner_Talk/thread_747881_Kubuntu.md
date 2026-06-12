---
title: "Kubuntu"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by D|F on 2008-04-07
I was finish installed Kubuntu desktop. When i reboot my system and i get Kubuntu login screen i put username and password, but my pass is incorrect, i cannot open it. please tell me what i have to do? I cannot open my Ubuntu now...

---

### Post by SunnyRabbiera on 2008-04-07
weird, did you put in the same password you had for ubuntu?
its the same password.
just remember the password is case sensitive.

---

### Post by bodhi.zazen on 2008-04-07
Make sure it is not something simple like the caps lock being ON.

If that fails look here : [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

---

### Post by D|F on 2008-04-07
Yes, of course i put the same password. and im sure im not open caps lock. There is two username. First is 

Sabayon User
Sabayon-Admin

and the second is my username

darknessfall.

There is the way for me to open it?

---

### Post by SunnyRabbiera on 2008-04-07
wait, you were using sabayon?
what did you do to install kubuntu?
were you using sabayon before going over to kubuntu?

---

### Post by D|F on 2008-04-07
Yes, i dont know about sabayon, fater i finish install Kubuntu, when i enter to Kubuntu login screen Sabayon username is there, and second usernam is my username. When i insert the pass, its opened teh terminal box.

one of user in Ubuntu IRC chat tell me how to install Kubuntu desktop. Its like:

Ctrl+Alt+F1-8
then
sudo apt-get install kubuntu-desktop

i did that, and now i cannot open my Kubuntu...
please tell me what i have to do...
i dont have window, the only hope is i can open my Ubuntu again...

---

### Post by SunnyRabbiera on 2008-04-07
really weird.
I was about to say if you were a sabayon user and tried to install kubuntu over it then no wonder why you had issues if you put kubuntu on the same partition on it.
maybe you should use a live CD, assuming you have a CD burner

---

### Post by D|F on 2008-04-07
Owh ... But i dont have live Cd, i was download Ubuntu from [www.ubuntu.com](www.ubuntu.com), and i install it. There's no other way to fix my problem?

---

### Post by D|F on 2008-04-07
or i have to reinstall my Ubuntu?

---

### Post by bodhi.zazen on 2008-04-07
How did you install kubuntu if not from a iso file burned to a cd (or DVD image)?

If you do not know the password you can try booting to the recovery mode and setting a password from there.

Otherwise you can use chroot. Boot any live cd/dvd (Sabayon will do), mount your ubuntu root partition at /mnt

then become root

and 

```
chroot /mnt /bin/bash
passwd user
```

where user = your ubuntu log in name.

---

