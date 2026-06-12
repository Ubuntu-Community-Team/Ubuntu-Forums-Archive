---
title: "Grub"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by glenduncanscott on 2006-10-03
Hi, 

I'm unable to boot into Ubuntu at present. This is a result of trying to solve a possible clocking problem and making the following changes:

```
sudo gedit /boot/grub/menu.lst
```

edited line 
```
# kopt=root=/dev/hdc2 ro 
```

with
```
# kopt=root=/dev/hdc2 ro clock=pmtmr notsc
```

then 
```
sudo update-grub
```

Rebooted and now presented with a blank screen. I'm still a noob when it comes to Grub, but is it possible to edit the /boot/grub/menu.lst and remove this entry from the grub> command promt?

Any help would be greatly appreciated ](*,)

---

### Post by xyz on 2006-10-03
If you cp your /boot/grub/menu.lst, try restoring it as it was.
See what happens.

---

### Post by glenduncanscott on 2006-10-03
That is exactly what I'm trying to do but unable to access/edit it.

In hindsight what I should have done before editing was:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

then access the grub menu and press 'c' for commmand prompt

```
grub>configfile /boot/grub/menu.lst_backup
```

this would have then loaded/booted the original configuration file! We live and we learn.

Back to the point...There must be a way???

---

### Post by xyz on 2006-10-03
Hi-
From what I understand you're trying to 
sudo gedit /boot/grub/menu.lst...that is to edit it as you say. But no access!
I was wondering whether you made an exact copy of your /boot/grub/menu.lst...in that case you could restore it as it was before.
Sorry if I didn't understand!

---

### Post by glenduncanscott on 2006-10-03
No worries, I normally do make a copy but for some odd reason this time I didn't.

---

### Post by xyz on 2006-10-03
> **glenduncanscott said:**
> No worries, I normally do make a copy but for some odd reason this time I didn't.

No problem...try this then...let me know! Good luck:

[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

---

### Post by ajgreeny on 2006-10-03
If you use the live CD to boot into a live session and then mount the ubuntu partition and open the menu.lst file, you should be able to edit the line back to what it was by removing the
 clock=pmtmr notsc
from the end of the line.  I can not remember if you get root access with the live CD, but I'm pretty sure there is a way to get it if you're not root by default.  Anyone else know the details?

---

### Post by glenduncanscott on 2006-10-03
> **xyz said:**
> No problem...try this then...let me know! Good luck:

[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

Ok step 4 asks you to mount the appropriate linux partions which are already mounted, so no action was taken. Then the next page lists the partitions with a reformat tick box beside each. I unticked each box then after this the proposed changes are listed and you press install. Then I was hoping to reach step 6 or 7 instead the installation process began!! Then after about 15% I recieve this error message:

We're sorry; the installer crashed. Please file a bug report at [https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug](https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug) and a developer will attend to the problem as soon as possible. To help the developers understand what went wrong, include the following detail in your bug report, and attach the files /var/log/installer/syslog, /var/log/syslog, and /var/log/partman:

Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 130, in ?
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 55, in install
    ret = wizard.run()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 266, in run
    self.process_step()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 741, in process_step
    self.mountpoints_to_summary()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 1029, in mountpoints_to_summary
    self.progress_loop()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 538, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s; see "
RuntimeError: Install failed with exit code 1; see /var/log/installer/syslog and /var/log/syslog


The future looks very bleak indeed...

---

### Post by glenduncanscott on 2006-10-03
> **ajgreeny said:**
> If you use the live CD to boot into a live session and then mount the ubuntu partition and open the menu.lst file, you should be able to edit the line back to what it was by removing the
 clock=pmtmr notsc
from the end of the line.  I can not remember if you get root access with the live CD, but I'm pretty sure there is a way to get it if you're not root by default.  Anyone else know the details?

Using the Live CD I've tried 

```
sudo -s -H
``` 

which appears to give root access to the CD but not to the system.

Mounting was unsuccessful

```
sudo mount /dev/sda1
```

and will not allow me to run fstab either...

```
sudo /etc/fstab
```

The future looks bleak :(

---

### Post by xyz on 2006-10-03
Don't despair too much glenduncanscott!
Look at these. (or reinstall?):
> This section explains how to rescue GRUB (the GRand Unified Boot loader), using the Ubuntu alternate/install CD ROM.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

On that page, you'll get a clear solution using the following:

- Using the Ubuntu Alternate/Install CD

- Using the Alternate/Install CD and Overwriting the Windows bootloader
(you've already tried that one so...)

- Using the Ubuntu Desktop/Live CD

- Using the Unofficial "Super Grub Disk"

The "Troubleshooting" section near the bottom of the page may be of interest as a first reading!

I'm sure you'll find a way...one way or the other and you'll have a backup handy as soon as you get it fixed, right?
Hang in there!

---

### Post by bulldog on 2006-10-03
Is your system intact and is the only trouble to get grub reinstalled?

If so, that's fixed in ten minutes.

Just let me know.:D

---

### Post by glenduncanscott on 2006-10-03
> **xyz said:**
> Don't despair too much glenduncanscott!
Look at these. (or reinstall?):

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

On that page, you'll get a clear solution using the following:

- Using the Ubuntu Alternate/Install CD

- Using the Alternate/Install CD and Overwriting the Windows bootloader
(you've already tried that one so...)

- Using the Ubuntu Desktop/Live CD

- Using the Unofficial "Super Grub Disk"

The "Troubleshooting" section near the bottom of the page may be of interest as a first reading!

I'm sure you'll find a way...one way or the other and you'll have a backup handy as soon as you get it fixed, right?
Hang in there!

If you knew how many times I had to rebuild Ubuntu with this sub standard piece of Windows laptop hardware you´d despair aswell. 

This problem arose trying to solve another major issue:
[http://www.ubuntuforums.org/showthread.php?t=265286](http://www.ubuntuforums.org/showthread.php?t=265286)

So even if I resolve this issue with some fancy grub command or spend the next 3 hours reinstalling and tweaking I&#314;l still be facing a brick wall!

It makes me wonder whether some machines should be purely dedicated to Windows and nothing more.

Sorry for my rant, and thanks so much for your input I´ll see if I have any joy tomorrow, when I´m in a better frame of mind :mad:

---

### Post by glenduncanscott on 2006-10-03
> **bulldog said:**
> Is your system intact and is the only trouble to get grub reinstalled?

If so, that's fixed in ten minutes.

Just let me know.:D

As far as I know I think the system is still intact, but cannot be 100% sure after trying to reinstall grub unsuccessfully. See above error message.

If you can add anything in addition to:
[Recovering Ubuntu After Installing Windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
I´d be glad of your assistance.

---

### Post by bulldog on 2006-10-03
Well we can do two things.

First to try to recover your menu.lst and if this fails we reinstall GRUB.

Boot the Ubuntu live cd and the we go to mount your existing Ubuntu.
Hope you know on which partition it is installed?

When you're booted into the live cd we make a mounting dir ```
sudo mkdir /mnt/rescue
```

Then we mount the existing ubuntu [hope you know which partition it's installed]
```
sudo mount /dev/??? /mnt/rescue
```

If you have no idea what your Ubuntu partition is try ```
sudo fdisk -l
``` l as in like
So we can have a peek at your partitions to see if Ubuntu is among them :D

If this is succesfull we can acces the menu.lst by ```
gksudo gedit /mnt/rescue/boot/grub/menu.lst
```

---

### Post by glenduncanscott on 2006-10-03
> **bulldog said:**
> Well we can do two things.

First to try to recover your menu.lst and if this fails we reinstall GRUB.

Boot the Ubuntu live cd and the we go to mount your existing Ubuntu.
Hope you know on which partition it is installed?

When you're booted into the live cd we make a mounting dir ```
sudo mkdir /mnt/rescue
```

Then we mount the existing ubuntu [hope you know which partition it's installed]
```
sudo mount /dev/??? /mnt/rescue
```

If this is succesfull we can acces the menu.lst by ```
gksudo gedit /mnt/rescue/boot/grub/menu.lst
```

You have made my day :D You beauty! Top Dog 8) Your the man! My systems back!!! 

Sorry for the delay but the Live CD takes forever on that [machine]("https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteProA100").

Those commands worked a treat, thankyou so much! 

Now back to that other problem of system freezes...:-k

---

### Post by bulldog on 2006-10-03
It seems your RAM is not to bad, did you concider to take a look at your hdd?

If the hdd is dying or have severe breakups it could explain why windows is less sensitive to it.

Windows will locate the bad sectors and write around them,don't know however how Ubuntu handles this kind of misbehavior.

Take a look at the webpage of the manufacturer and see if there is a checking tool available.

---

### Post by glenduncanscott on 2006-10-03
> **bulldog said:**
> It seems your RAM is not to bad, did you concider to take a look at your hdd?

If the hdd is dying or have severe breakups it could explain why windows is less sensitive to it.

Windows will locate the bad sectors and write around them,don't know however how Ubuntu handles this kind of misbehavior.

Take a look at the webpage of the manufacturer and see if there is a checking tool available.

There´s a basic PC diagnostic tool and utilities software packages available for Windows XP, but I´ve removed Windows XP (with no intention to reinstall), so are there any Linux apps that could do the job better?

---

### Post by bulldog on 2006-10-03
Well I used always the application which is provided by the manufacturer.

I have a dual boot :D  no problem to use those.

You can see at their webpage if there's a DOS version you can install on a floppy.

You run this programs mostly at boot up so your hdd can reached without a OS loaded.

If there's a Linux app I don't know you have to see by yourself.

---

### Post by glenduncanscott on 2006-10-03
Oh the days of floppy, now modern laptops only have CD drives installed :-| 

Found [Aaron Talbot´s]("http://yhslug.tux.org/docs/hdtest.htm") page very helpful.

Ok booted up Live CD again as filesystem must NOT be mounted. 

Tested sda1 by typing:

```
e2fsck -c -C -y /dev/sda1
``` 

Ran this Read Only test 3 times and everytime the system hangs at a random point and does not complete the test. Results:

1) Only tested 607296/ of 9628951 blocks
2) Only tested 584384/ of 9628951 blocks
3) Only tested 983168/ of 9628951 blocks

Could this be pointing to a stuffed hdd? Do you think I need to reinstall Windows to reconfirm this data before returning to the manufacturer for repair/replacement? 

I might be finally getting somewhere :)

---

### Post by bulldog on 2006-10-03
Don't break out the bottle yet :D 

It's possible your hdd is dying or is damaged.

But it could be also your RAM what's playing with you.

To be sure you should replace one by one the hardware to be sure what course the malfuction.

If you have support for your hardware I should mail them to see what they say.

If it's an older computer you only can try to exchange the hardware.

---

### Post by glenduncanscott on 2006-10-03
> **bulldog said:**
> Don't break out the bottle yet :D 

It's possible your hdd is dying or is damaged.

But it could be also your RAM what's playing with you.

To be sure you should replace one by one the hardware to be sure what course the malfuction.

If you have support for your hardware I should mail them to see what they say.

If it's an older computer you only can try to exchange the hardware.

Thanks for your speedy reply.

I was hoping that running a 24 hour memtest had eliminated the RAM issue, but it´s a valid point. Hopefully have a chance to test some new RAM when it arrives in the post.

The Toshiba laptop is less than 6 months old so I´ll email customer services and see what they have to say.

Thanks so much for you help today, really appreciate it :-D

---

### Post by glenduncanscott on 2006-10-04
Spoke with Toshiba Customer Services and they requested I reinstall Windows XP and run the Diagnosic Tools. This unfortunately produced no errors. Also performed a CHKDSK and despite taking some time, completed successfully with no errors reported.  

Now I know Windows is still operable around faulty disc sectors but if there had been a problem with the hdd should't this have been displayed in the scan reports? Also the RAM never froze once. Are there any other tests that can be performed to eliminate any hdd or RAM suspisions? 

Any thoughts and suggestions gratefully received once more.

---

### Post by devils_casper on 2006-10-04
the best option is [UBCD]("http://www.ultimatebootcd.com/download.html"). it scans harddisk and RAM, and has a lot of tools to fix errors.




casper

---

### Post by glenduncanscott on 2006-10-04
> **devils_casper said:**
> the best option is [UBCD]("http://www.ultimatebootcd.com/download.html"). it scans harddisk and RAM, and has a lot of tools to fix errors.
casper

Thanks Casper, great set of utilities, just running some tests now, hopefully will find some hard evidence.

---

### Post by bulldog on 2006-10-04
Back again :D 

When your computer freezes is there something strange happening,like 100% CPU load?

It could be a proces running in the background what is the reason of this.

If you have done a 24 hour memtest, it's not likely that there are errors in your RAM.

If your hdd gives no errors we can assume this device is correct too.

Did you install the drivers for your graphical card?

Do you have a not common peace of hardware in your computer which is not properly recognized?

Some thought's ,it can be almost anything.

Had a computer once which was randomly rebooting,sometimes 3 times a day and sometimes once a week.
Couldn't get it straight,many times new install and no joy.
It had a VIA chipset and every time I set up the latest drivers.
At last no drivers installed and never had a trouble again.

So basicly if you have troubles it can be the slicest thing.

---

### Post by glenduncanscott on 2006-10-04
Hi Bulldog, good to hear from you again.

Yes the CPU (Intel Celeron M processor 360) does run high and yes freezes with too many apps open. Normally run Firefox, Thunderbird, Gaim, Amarok and Firestarter. 

Having said that all applications appear unresponsive during this phase so it´s doubtful that I would be able to obtain any useful information from the system monitor. 

Still trying to perform some further tests on the hdd. Spoke a little too soon when experimenting with Ultimate Boot CD, as it works perfectly on my desktop machine but on the Toshiba laptop many of the apps will not open or just freeze! It interesting to note that many of the apps appear to disagree with my ATI Radeon® Xpress 200M graphics card. 

It´s reported in the [installation guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") that I followed that OpenGL seems to be broken for the R200 cards! Although the installation appears to work since I obtained the correct result and rendering, but maybe this card is causing conflicts? Would you suggest removing the driver and monitoring the performance? 

This is a very difficult problem to resolve as it´s not consistent, sometimes the system can freeze after login, many times installing apps or after some random period of time and for no apparent reason.

The only thing I can remember thats not detected is the Windows Modem.

Have you heard of problems with the Phoenix BIOS? Apart from not being supported by Fnfx or Toshiba linux Utilities.

Some more food for thought ;)

P.S. Tomorrow I&#314;l be disappearing away from my PC to the sound of wedding bells, bag pipes and the great outdoors, returning next week to pursue these problems once more. CU ;)

---

### Post by glenduncanscott on 2006-10-16
After another rebuild with no drivers installed system still froze with no explaination. It would appear this system is not linux compatiable. After 4 months of fustration I'd had enough and sold it today...problem solved! Thanks for all you input.

---

