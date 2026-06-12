---
title: "Ubuntu 6.06 LTS RC to Ubuntu 6.06 LTS Final"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by apt on 2006-05-30
I have installed Ubuntu 6.06 LTS RC version (couldnt wait :)  ) will I be able to do a online update to the Final version or do I need to re-download and re-install Ubuntu 6.06 LTS Final?

Many Thanks

Adrian

---

### Post by TrendyDark on 2006-05-30
The change from the release canidiate and the final version won't be drastic, so I'd imagine you'll be able to update any packages via synaptic/apt-get fairly easily.

---

### Post by henriquemaia on 2006-05-30
[quote=apt]I have installed Ubuntu 6.06 LTS RC version (couldnt wait :)  ) will I be able to do a online update to the Final version or do I need to re-download and re-install Ubuntu 6.06 LTS Final?

Many Thanks

Adrian[/quote] 
You can do an online update. 

You just have to open a terminal and type:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

After that process, you'll be running the latest version.

---

### Post by apt on 2006-05-30
many thanks for your quick responses... I have noticed a number of software updates available since I installed RC, does this meant that its already updating itsself to the final version?

Adrian

---

### Post by Gustav on 2006-05-30
Yes.

---

### Post by henriquemaia on 2006-05-30
[quote=apt]many thanks for your quick responses... I have noticed a number of software updates available since I installed RC, does this meant that its already updating itsself to the final version?

Adrian[/quote]

The updates are going to be very frequent until the final release since Dapper is still under development. I guess one can say that it is already updating towards the final release.

---

### Post by nocturn on 2006-05-30
You should be notified automaticly when updates are available.  Just install them and you will be fine.

have fun.

---

### Post by apt on 2006-06-01
How to I check my version of Ubuntu has been sucessfully updated to Ubuntu 6.0.6 Final.  Is there a terminal line I can run to check?

I havent got any updates for the RC version in the last few days.

Adrian

---

### Post by ubuntu_demon on 2006-06-01
[QUOTE=apt]How to I check my version of Ubuntu has been sucessfully updated to Ubuntu 6.0.6 Final.  Is there a terminal line I can run to check?

I havent got any updates for the RC version in the last few days.

Adrian[/QUOTE]

Just announced on fridge.ubuntu.com : Dapper is out!

$ sudo apt-get update
$ sudo apt-get dist-upgrade

If you have done that then you are running final. 

see also this thread :
[http://www.ubuntuforums.org/showthread.php?t=185693](http://www.ubuntuforums.org/showthread.php?t=185693)

---

