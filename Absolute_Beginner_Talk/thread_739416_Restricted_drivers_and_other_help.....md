---
title: "Restricted drivers and other help...."
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by Lichig0 on 2008-03-29
To make a long story short, Hard drive with Ubuntu failed,I installed Ubuntu in place of Windows

Well now that I have Ubuntu installed on a different hard drive i wanted to configure it the way i had it....but its not as easy as last time.....

CNR couldn't install libgt4-gui

I cant enable Extra visual effects: The software source for the package

   nvidia-glx-new

 is not enabled.

and NVidia binary X.Org driver ('new' driver) cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.------i have never got this message before and now i cant find anything that doesnt have this error....i dont know what to do...

---

### Post by Daveth on 2008-03-29
have you been into system/admin/restricted drivers manager, and added the Nvidia driver (assuming you have an nvidia graphics card, of course!). Or you can use the Envy script @

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

you will not get anywhere with desktop effects without the 3d acceleration being enabled.

---

### Post by Lichig0 on 2008-03-29
I never had this problem before but if i try to enable the restricted driver i get:

The software source for the package

   nvidia-glx-new

 is not enabled.

---

### Post by compiledkernel on 2008-03-29
Ignore the use of CNR. 

Rather make sure that you have nvidia-glx-new installed via 

sudo aptitude install nvidia-glx-new 

Once thats been done, then run 

sudo nvidia-xconfig

and restart X (ctrl-alt-backspace) , you should then see an nvidia splash screen.

---

### Post by rkd on 2008-03-29
The error message you mention when you try to enable extra visual effects makes me think you don't have the usual Ubuntu repositories enabled.  Have you checked System > Administration > Software Sources and verified that all the usual Ubuntu repositories are checked?

---

### Post by Lichig0 on 2008-03-30
Ok, i went to install Windows and well it formated the wrong Hard dive...so i Re-installed Ubuntnu and well everything works fine now, i don't know whats different but it works so i no longer need help. :)

---

