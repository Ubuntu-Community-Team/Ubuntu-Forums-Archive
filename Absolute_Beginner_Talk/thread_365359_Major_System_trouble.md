---
title: "Major System trouble"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by Dannybzr on 2007-02-19
Hello all,

Just new to the whole Linux thing, thats why I'm in trouble!!!

I am in bad need of some help, I have just tried to partition my harddrive using partition magic, and my system wont boot up now,I'm just getting a blue screen. 

I tried to partiton the NTFS partition that windows is installed on and I wanted to create a partition that I could install Ubuntu on. 

I placed the partition on after the NTFS one and placed the Linux swap file before the Ubuntu one and after the NTFS one. Then I hit return and the system went to reboot, a screen came up and showed that it was doing 1 of 4 operations(partition magic). the machine didnt boot, then the screen did not finish the 4 operations. 3 failed and now my machine will boot as far as the windows xp logo and then the blue screen shoots up.

I have my xp disk which I can boot from but that will only get me to the recovery console.

Before anyone asks, Yes I was that stupid to do this without rescue disks

All the help would be much appreciated..

Regards

Danny

---

### Post by xopher on 2007-02-19
Partition Magic seems to have corrupted something. I'd boot up the Ubuntu Live/Install CD and mount the NTFS partition -- And save all data you can. Hopefully it's still there.

Then I believe there aren't many alternatives to either try and reinstall Windows with or without formatting the drive.

---

### Post by Dannybzr on 2007-02-19
I cant boot from the Ubuntu live cd, it dosent even reach the logo screen.

---

### Post by jvc26 on 2007-02-19
Have you checked the md5 of the iso (if you downloaded the iso) and have you run the error check on the cd as the live cd may well be a bad burn or a faulty download which may be why it doest boot.
Il

---

### Post by richardjennings on 2007-03-01
I am experiancing a similar problem. I used partition magic / screwed my machine. So far I have managed to get XP up and running again without re-installing. Ubuntu is proving a little more difficult. It is currently hanging on drivers/usb/input/hid-core.c:v2.6:USB HID Core driver , if you have any clue how to fix that.

To get xp running.... boot up xp cd, goto recovery console and run chkdsk c: /f

This will fix any problems with the drive. You might want to just run chkdsk c: initially so that you can see what will be 'fixed' before it happens.

Once i had done this, i started getting a new error with hal.dll

to fix this, again recovery console, 

DEL C:\Boot.ini
BootCfg /Rebuild
Fixboot

and you should have xp available to boot.

To get the grub menu back for Ubuntu, you need to boot the live cd. If you cant boot the live cd i dont know how to do it :/ 

If you mae it into live cd enviroment goto terminal

sudo grub

find /boot/grub/stage1                        - this should return hd(x,y)

replace x,y with the numbers returned from the previous code.

root (hdx,y)

setup (hd0)

quit

reboot the system (without live cd) and hopefully grub should appear with boot options.

This is how far i have got. But - I still have this problem with Ubuntu not booting - even wont boot into recovery mode. AHHHH.

---

