---
title: "White Screen on Boot with 7.10 on iMac G5"
date: 2007-11-08
forum: Apple PPC Users
---

### Post by Giles on 2007-11-08
iMac G5 (Rounded back, Rev B i think, no isight) with ATI Radeon 9600

I chucked in the install Cd and after choosing live-powerpc64 i got a white screen so i rebooted and added video=ofonly and it booted into the livecd fine. i then installed ubuntu, when i try to boot from the hard drive i get the white screen again, i tried Linux single and that gave me the same thing.

so i booted from the livecd again to edit my yaboot.conf but my drive /dev/sda5 refuses to mount.

edit: ok so this time i managed to mount but editing yaboot.conf to remove "splash" from the Linux boot parameters and running 
> sudo /mnt/usr/sbin/ybin -C /mnt/etc/yaboot.conf
was successful but when i reboot the changes don't seem to appear in yaboot, they stay in the file but i changed the timeout, colours and defaultos and none of it seems to have registered. any ideas?

---

### Post by ppc_guy on 2007-11-08
Just a shot in the dark here... But as a mac user and a mac tech. Did you keep up on all your firmware updates? Like I said, could just be a shot outta left field.


Nathan
---------------------------------------------------------------------------------------
When you are Sierra-Oscar-Lima. I'm Hotel-Tango-Hotel
---------------------------------------------------------------------------------------

---

### Post by Giles on 2007-11-08
> **ppc_guy said:**
> Just a shot in the dark here... But as a mac user and a mac tech. Did you keep up on all your firmware updates? 
hey nathan thanks for the reply, i'm assuming you mean official apple firmware updates, i have the latest version of tiger 10.4.10 installed on a 130GB partition of my HD with a 10GB partition for ubuntu and a 400MB or so swap drive. i have kept up to date with all the system updates, and theres a lot of outstanding stuff but it's just software. i think there has recently been a few imac firmware upgrades but they are for newer (intel and up i think) imacs.

if you mean some other sort of firmware update i don't know about it then by all means, enlighten me.

---

### Post by indiworks on 2007-11-08
Not sure if this helps, but I am also on an iMac G5 and just downloading 7.04 since I read here [http://ubuntuforums.org/showthread.php?t=427714&page=4](http://ubuntuforums.org/showthread.php?t=427714&page=4) that

"After many hours of burning, booting and googling, I finally figured it out:
Ubuntu Gutsy 7.10 simply doens't work on Mac/Powerpc!!
Feisty 7.04 does!"

---

### Post by colinhayes on 2007-11-08
> **indiworks said:**
> \"After many hours of burning, booting and googling, I finally figured it out:
Ubuntu Gutsy 7.10 simply doens't work on Mac/Powerpc!!
Feisty 7.04 does!"

bah humbug!  It just has a steep learning curve.

---

### Post by Giles on 2007-11-09
ok so i'm all sorted out here.

what i did was actually quite simple, i booted my installation and added "video=ofonly" now this may seem stupid but according to the yaboot.conf it was already being appended, this brings me to the problem i was having. booting from the livecd to edit yaboot and then running:
> sudo /mnt/usr/sbin/ybin -C /mnt/etc/yaboot.conf
did not work for me! (/mnt is just where i mounted my filesystem)

however once i appended the video=ofonly to the boot i was able to successfully run ybin and now yaboot does it for me :D

sorry for any timewasting and i hope this helps someone out. if you need/want any more deatils feel free to ask

giles

---

