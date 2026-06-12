---
title: "How do I get rid of Windows XP Home?"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by wedshot on 2007-03-08
I'm running Daper Drake on a Dell 9100 along with Windows XP Home.  I've come to my sences and I want to get windows off my box.  I'm not concerned with saving anything from the windows partition.  Is there a way to reformat the Windows partitions so I can use the space for Linux without doing a complete reinstall?
Thanks,
Roger

---

### Post by oilchangeguy on 2007-03-08
you should be able to use gparted, which is on the live cd to delete the partition. i don't know if after doing that if you can take the space and add it to ubuntu, or just have an empty partition for storage.

---

### Post by annda on 2007-03-08
after deleting the windows partition with gparted, you can expand the ubuntu ext3 partition to fill the disk and/or add another one for file storage or /home. whatever you want!

i think it's a good idea to have a seperate partitions for backups, so you can create one with the size of a couple GBs (or more, if you need multimedia files).

having a separate /home partition is good if you need to reinstall with exactly the same configuration. if you like to experiment and try things out, set up a backup and storage partition.

---

### Post by ajgreeny on 2007-03-08
Just remember that if you have grub on the MBR of your windows partition, you will remove grub when you delete that partition with gparted (or any other partition manager software.  Don't be too concerned about this, however, though it is rather horrifying when you find nothing will boot.

What you need to do is the following:-

Boot into the ubuntu live CD
open a terminal and run :
    sudo grub
This gets you to a simple grub command line.
Then:
    find /boot/grub/stage1
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
    root (hd?,?)
[like : root (hdo,1) ,probably]
then:
    setup (hd0)
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    quit
Finally reboot, and hopefully you will now have a working grub bootloader.

I hope this all makes sense to you and good luck.

---

### Post by wedshot on 2007-03-09
ajgreeny: Following your instructions, I got to the grub command line but when I typed in : find/boot/grub/stage1 I got error message 27 which is an unrecognized command.  Before I get to the command line I get a 'failed to start x server' .  This can get very confusing to say the least.

---

### Post by Crooksey on 2007-03-09
> **ajgreeny said:**
> Just remember that if you have grub on the MBR of your windows partition, you will remove grub when you delete that partition with gparted (or any other partition manager software.  Don't be too concerned about this, however, though it is rather horrifying when you find nothing will boot.

What you need to do is the following:-

Boot into the ubuntu live CD
open a terminal and run :
    sudo grub
This gets you to a simple grub command line.
Then:
    find /boot/grub/stage1
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
    root (hd?,?)
[like : root (hdo,1) ,probably]
then:
    setup (hd0)
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    quit
Finally reboot, and hopefully you will now have a working grub bootloader.

I hope this all makes sense to you and good luck.

If Ubuntu and XP are on the same partition this wont matter. Its fine to just delete it.

*** grub is installed on /dev/sda

it wont affect /dev/sda1 windows /dev/sda2 linux will still boot.

---

### Post by ajgreeny on 2007-03-09
> **Crooksey said:**
> If Ubuntu and XP are on the same partition this wont matter. Its fine to just delete it.

*** grub is installed on /dev/sda

it wont affect /dev/sda1 windows /dev/sda2 linux will still boot.

You can't have both windows and ubuntu on the same partition.  The same disk, maybe but not the same partition.

---

### Post by wedshot on 2007-03-09
Yes they are on the same disc but different partitions.  I was going to just reload Daper Drake and reformat the whole disc but that didn't work.  That's what I want to do but I can't seem to get it right.  I'm also trying to run two monitors on this Dell box but all I can get them to do is mirror each other.  I guess it's just not my day.  Any help would be apperciated.
Thanks, wedshot

---

### Post by lamalex on 2007-03-09
why didnt just reloading the whole thing work? that should be the only 100% failsafe solution. Just pop in dapper, and when it comes to formatting choose use the entire disk. or if you really want do partition table by hand, delete everything, and then make 1 big one, or however you want your setup to be.

---

### Post by ajgreeny on 2007-03-09
What went wrong when you tried to reformat and start again with the reinstallation of ubuntu.  It should work without any problem if you let the install disk do everything according to the defaults, unless, of course you have one of the pieces of hardware that seem to present problems.

Do a search on problem motherboards and chipsets to see if that helps.

---

### Post by wedshot on 2007-03-10
I've managed to rid myself of Bill's OS but to do it I had to load a copy Suse 10.0.  That loaded like a dream so I used it to reformat the HD.  Now the whole drive belongs to Linux.  I still have the problem of getting Ubnutu to load.  I downloaded  6.10 from the Ubuntu site and followed the install instructions but it still hangs up with the prompt "Failed to start the X Server".  So I guess I'm half way there but I've been at this all day .  I really do prefer Ubuntu to Suse.  I'm just not sure what to do next.  Help Please.
Wedshot

---

### Post by wj32 on 2007-03-10
Try reinstalling Xorg or if that doesn't work, rescue your data and do a complete reinstall.

---

### Post by STREETURCHINE on 2007-03-10
go into recovery and reconfigure your xorg.conf.


      ```
sudo dpkg-reconfigure xserver-xorg
```

answer the questions ,if you are not sure just accept the defaults

      then

     ```
sudo apt-get update
```

    restartx
  
      ```
startx
```

---

### Post by wedshot on 2007-03-10
Thanks:  That worked with the 6.06 version.  Now my only problem is getting both monitors doing something other than mirror each other.  Thanks again for all the help out there, kinda makes me feel at home.
Wedshot

---

### Post by STREETURCHINE on 2007-03-10
cant help you with that one sorry..


i would close this thread put resolved on it and start a new one specific to your duel monitors

---

### Post by wedshot on 2007-03-11
Here's a stupid question.  How do I close this thresd?

---

### Post by xyz on 2007-03-11
> **wedshot said:**
> Here's a stupid question.  How do I close this thresd?
You can mark it [RESOLVED] if that's what you mean.
Go to your 1st post, click on Edit and tick Resolved > Save.

---

