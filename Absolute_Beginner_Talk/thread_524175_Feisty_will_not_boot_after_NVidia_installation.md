---
title: "Feisty will not boot after NVidia installation"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by Chamelion on 2007-08-12
I am dual booting Windows XP and Feisty and have installed a NVidia GeForce FX 5200 yesterday. The Windows drive works without any problems. Unfortunately the Ubuntu drive does not boot anymore. I still get the option to boot into XP or Ubuntu. When I choose Ubuntu the boot screen still comes up. Then the monitor turns black.
I tried to start in safe mode. After typing startx the same thing happens.
Installed Grub again with Super Grub Disc. No change.
The Feisty Live CD still works without any problems.
If anybody has a solution, could you please be very detailed as I am still very new to this sort of thing and have very limited knowledge.
The only other thing I can think about is to re install Feisty and hope for the best.:(
Thank you very much in advance.:)

---

### Post by jimrz on 2007-08-12
> **Chamelion said:**
> I am dual booting Windows XP and Feisty and have installed a NVidia GeForce FX 5200 yesterday. The Windows drive works without any problems. Unfortunately the Ubuntu drive does not boot anymore. I still get the option to boot into XP or Ubuntu. When I choose Ubuntu the boot screen still comes up. Then the monitor turns black.
I tried to start in safe mode. After typing startx the same thing happens.
Installed Grub again with Super Grub Disc. No change.
The Feisty Live CD still works without any problems.
If anybody has a solution, could you please be very detailed as I am still very new to this sort of thing and have very limited knowledge.
The only other thing I can think about is to re install Feisty and hope for the best.:(
Thank you very much in advance.:)

feisty is still apparently trying to use your old xorg.conf which, of course, will not work with the new card. boot in to safe mode, login then type in 
```
sudo dpkg-reconfigure xserver-xorg
```
follow the prompts, you can probably accept the defaults for most everything unless you see something that you know for sure needs to be different then either reboot or type
```
sudo /etc/init.d/gdm restart
```

---

### Post by Chamelion on 2007-08-12
Thank you
I followed everything exactly, but unfortunately I am ending up with a black screen again.:confused::(

---

### Post by coffee-n-cream on 2007-08-12
im having the same problem too but im using 8800gts.tried using restricted driver manager and envy to install the nvidia drivers and after booting up,i got a error msg: no screens found.if i use automatix i only got a black screen.then i tried downloading FF for amd64.burned it successfully n when i try to install it,after the vmlinuz loading thingy,all i got is a black screen.no ubuntu logo with the loading bar..its juz driving me crazy.btw my rig specs is DFI Lanparty SLI-DR,AMD 3700,eVGA 8800gts SC,2gig ram,hitachi desktar500gb(for windows) n WD 160gb(for linux) any help would be appreciated..

---

### Post by nalinde on 2007-08-12
Ok, have you done a install with Nvidias Commercial driver or do you have their latest drivers? If not, try this.... :-)

I like to use [Alberto Milones software Envy]("http://www.albertomilone.com/nvidia_scripts1.html") to install my nvidia drivers. BTW he's the man ;-D

1. First of all, log in trugh safe mode and make sure that you are in your home catalouge by simply  typing *cd*
2. Then type this *wget [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu6_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu6_all.deb)*
This will download the .deb to your home catalouge. If you want to know more about wget, type *man wget*.
3. Now to the installation, type: [I]sudo dpkg -i envy_0.9.7-0ubuntu6_all.deb
[/I]. and just type in your password.
4. Now Envy is installed to your computer. Lets run it! :-D *envy -t* The -t means that you will run it in text mode. Then Just press 1 and hit enter to install the latest nvidia driver :-D.

So hope this will help you! ubuntu m8....

---

### Post by coffee-n-cream on 2007-08-13
> **nalinde said:**
> Ok, have you done a install with Nvidias Commercial driver or do you have their latest drivers? If not, try this.... :-)

I like to use [Alberto Milones software Envy]("http://www.albertomilone.com/nvidia_scripts1.html") to install my nvidia drivers. BTW he's the man ;-D

1. First of all, log in trugh safe mode and make sure that you are in your home catalouge by simply  typing *cd*
2. Then type this *wget [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu6_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu6_all.deb)*
This will download the .deb to your home catalouge. If you want to know more about wget, type *man wget*.
3. Now to the installation, type: [I]sudo dpkg -i envy_0.9.7-0ubuntu6_all.deb
[/I]. and just type in your password.
4. Now Envy is installed to your computer. Lets run it! :-D *envy -t* The -t means that you will run it in text mode. Then Just press 1 and hit enter to install the latest nvidia driver :-D.

So hope this will help you! ubuntu m8....

yup ive used envy but still no success.basically ive tried restricted driver manager,automatix,envy and downloading fr nvidia website and the error is still there.. :mad:

---

### Post by sparks0548 on 2007-08-13
You should still have the backup XORG.CONF.  When you are in the command screen, use Sudo and rename your xorg.conf to another name and name your XORG Backup file to XORG.CONF and then initiate the the gdm start command listed earlier.  I am not sitting in front on my machine right now and can't remember exactly.  

I renamed my XORG.CONF and was able to start X.  You can also move the file contents to the new file as well if you so desire.

---

### Post by Chamelion on 2007-08-13
> Originally posted by Nalinde
Ok, have you done a install with Nvidias Commercial driver or do you have their latest drivers? If not, try this....

I like to use Alberto Milones software Envy to install my nvidia drivers. BTW he's the man ;-D

1. First of all, log in trugh safe mode and make sure that you are in your home catalouge by simply typing cd
2. Then type this wget [http://albertomilone.com/ubuntu/nvid...buntu6_all.deb](http://albertomilone.com/ubuntu/nvid...buntu6_all.deb)
This will download the .deb to your home catalouge. If you want to know more about wget, type man wget.
3. Now to the installation, type: sudo dpkg -i envy_0.9.7-0ubuntu6_all.deb
. and just type in your password.
4. Now Envy is installed to your computer. Lets run it! envy -t The -t means that you will run it in text mode. Then Just press 1 and hit enter to install the latest nvidia driver .
I tried this, but I am getting an Error 404 message when I am trying to install through the commandline. Clicking on it on this computer (Working:)) is no problem. The computer I am working on belongs to a friend I am trying to convert to Linux LOL.
Considering the live CD still works, I might have to reinstall.
Sorry Sparks0548, your method is a little above my knowledge.

---

