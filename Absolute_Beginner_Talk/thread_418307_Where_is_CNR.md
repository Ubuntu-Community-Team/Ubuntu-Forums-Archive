---
title: "Where is CNR?"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by smoaky on 2007-04-22
Hi,
I have been waiting for the new version to come out so that I  can try out the  addition of CNR 
Where is it? :mad: I thought it was part of the newest version. I love 6.04, and 6.10 is OK, but CNR would be just icing on the cake for 7.04 :)
I am still runing "live CD" version 7.04  have not installed yet. would that not show CNR?
Thankx for any help ):P

---

### Post by Swab on 2007-04-22
I believe it will be released later on.  Don't think it will be officially supported.. it'll just be something you can download and install.

---

### Post by smoaky on 2007-04-22
Thanks Swab,
I have an Nvidia GeForce 6150 graphics card but am not able to change screen resolution from 800 X 600.
I am running 7.04 "live" not installed yet. could that be my prob? 
My system is running dual boot with XP Media Edition &  Vista Ultimate with AMD Athlon 64 X2  Dual Core 4200+ and 2 gigs Ram
Any SIMPLE solution? I'm still a noob to Ubuntu.](*,) 
Cheers

---

### Post by Swab on 2007-04-22
Wouldn't worry about it too much, it will be fixable after install I'm sure.

---

### Post by smoaky on 2007-04-22
COOL !!!!!!!!\\:D/ 
Anyone else out there able to fix this problem after installing  7.04 ?
Several answers/opinions  would be greatly appreciated. 
Waiting on the arrival of  my external  hdd enclosure so I can install Ubuntu on that external  hdd.
Until then I will have to wait to do an install. :-\"  Just trying to resolve any possible issues BEFORE install.
Thanks ;-)

---

### Post by evilgold on 2007-04-22
Ubuntu just made a deal with linspire for cnr a little while ago , and i think they are more focused on getting the paid version of linspire to work off ubuntu before they put CNR up for free.

---

### Post by SOULRiDER on 2007-04-22
Once you install, if the resolution doesnt fix itself you can try and change it from the control panel. If you cant do that, you can reconfigure xorg which isnt hard at all.

---

### Post by huygens on 2007-04-24
I think you can already try to reconfigure xorg within the LiveCD :-)
Try this command:
sudo dpkg-reconfigure xorg

I have only ATI card here, so I cannot tell you if it will be working or not for sure after the installation. My guess would be that if it does not work after the installation, you could try to install the Nvidia driver. This is now made really easy. Go to System -> Administration -> Restricted driver manager and you will find out by yourself ;-).
You could probably try that too from the Live CD and it case it requests you to reboot, just restart your X server. To do so, close all applications, log out (just like when you want to reboot, but choose the log out option) and press Ctrl+Alt+Backspace. After a while, you should see your login screen back. Log-in again and see if you can change your resolution. Probably you will have to do again this: sudo dpkg-reconfigure xorg

---

