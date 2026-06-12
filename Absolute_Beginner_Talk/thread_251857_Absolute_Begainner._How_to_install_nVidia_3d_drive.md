---
title: "Absolute Begainner. How to install nVidia 3d driver?"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by Jimit87 on 2006-09-06
Ok so now that i have Linux-Ubuntu 6.06.1 installed with help of few people from this forum, i now want to install nVidia 3D driver.

i have downloaded NVIDIA-Linux-x86-1.0-8774-pkg1.run from there website since i have 32bit comp. i copied this file to /home/username folder.

Now, What Do I Do From There?

i read few tutorials but didn't make any sense to me so teach me in baby steps.

Thank you.

---

### Post by encompass on 2006-09-06
Read the forums here first please... no reason to repost everything to you all over again.  A hint would be to search for a howto.  In particular, go for the Envy script... it is very easy to run.
But again I will say it, please search the forums first!

---

### Post by Jimit87 on 2006-09-06
i am sorry but i can't understand those tuts. i followed 1 tut from "How To" forum and it messed up my system, couldn't even get up to login screen and gave me some big blue screen error. so i need someone to explain me how to install the 3D driver i listed above on my system.

btw, i have nVidia MX 420.

so please, explain how to install this 3D driver onto my system so i can understand, baby steps. 

Thank you.

---

### Post by bodhi.zazen on 2006-09-06
> **Jimit87 said:**
> i am sorry but i can't understand those tuts. i followed 1 tut from "How To" forum and it messed up my system, couldn't even get up to login screen and gave me some big blue screen error. so i need someone to explain me how to install the 3D driver i listed above on my system.

btw, i have nVidia MX 420.

so please, explain how to install this 3D driver onto my system so i can understand, baby steps. 

Thank you.

Try this. Post error message if you get them (unlikely):
[How-to install nVidia Drivers in Ubuntu](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by omns on 2006-09-06
.

---

### Post by Jimit87 on 2006-09-06
Ok i will post my error mess. but it looks like i will have to reinstall Linux again. :confused:

---

### Post by encompass on 2006-09-06
Most times you don't have to reinstall linux.  We are not in the windows world here. :) Cheerup... Have you tried just using the NV driver?
```
sudo dpkg-reconfigure xserver-xorg
```
press enter if you want it to keep the defaults then when you have to select your video driver jsut select the nv driver.  Does that work for you?

---

