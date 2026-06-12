---
title: "New to Ubuntu, Video Card Issues"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by EndlessWaltz1026 on 2006-10-21
I decided to leave the Microsoft world and join you guys. But I am having some troubles setting up my Ubuntu. 

Type of Computer
Toshiba Satellite (Laptop)
1.6 Ghz Centrino Duo
2 gb of ram
120 gb hard drive
Intel Graphics Media Accelerator 950 

Ok, I didn't have much issues installing Ubuntu and getting it going. I am trying out Crossover Office to see if I can get World of Warcraft to work. It installed just fine but when I go to run it, it says "Your 3d accelerator card is not supported by World of Warcraft." 

My Device manager shows that my mobile intergrated graphics controller is from Intel but under device type it is unknown. 

Is there anyway to show Ubuntu what my card is? Or is there another work around to getting my graphics card to work?

I hope this doesn't sound confusing and I would great appreciate any answers that would help me. Thank you in advance.

---

### Post by broy on 2006-11-19
Are you using the i810 drivers?

---

### Post by jordanmthomas on 2006-11-19
To see which drivers you are using, look in /etc/X11/xorg.conf and find the appropriate section...just as a side note in case you didn't know.

---

