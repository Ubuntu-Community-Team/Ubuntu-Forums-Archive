---
title: "nVidia GeForce fx 5200, Dapper Drake"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by Taigrr on 2006-10-01
Okay, right now i'm on a fresh install of Dapper Drake! 

I have an NVIDIA GeForce fx 5200, and i'd like to get it working. I can see just fine, and right now my resolution is really high (Which is kinda cool!), but I have no acceloration. "glxgears" laaaaaags like apt-get upgrade on dial-up.

I searched around, but didn't find a very good starting point. So, knowing that i'm on a completely fresh install, I installed with the card plugged in and everything, where should I start?

---

### Post by Medieval_Creations on 2006-10-01
I had a similar issue... I have a GeForce fx 6200.  I tried downloading the latest drivers from Nvidia's site and compiling the module and it just seemed to break xorg every time.

I finally found this HOWTO: thread - [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

You will want to follow the instructions for installing nvidia-glx-legacy drivers.  Once I  installed and configured those like the HOWTO said it works great and has full 3D acceleration.

Give it a try... Hope it works out for you...

---

### Post by gn2 on 2006-10-01
The Nvidia driver can be installed with Automatix, along with codecs and other goodies which will make everything work.

It's all here: [http://www.getautomatix.com/](http://www.getautomatix.com/)

---

