---
title: "Ready to jump?"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by Shrek X on 2008-02-08
So, I just wanted to see if I am missing anything from one of the lunux gods. .  


I have a desktop computer, has two physical hard drives, one is a RAID drive, the other IDE.  I have my stuff backed up, and I want to load ubuntu on the RAID drive, vista is on the IDE already (both are internal to the system).  


I have run the liveCD and it works great, looks happy, etc.

Is there anything I should watch for before I install?  Anything I am missing?  Will the live CD handle leaving the windows partition alone and be able to boot to whichever I choose?  

Sorry if this is a very rudimentary question, and no specific hardware information,:its a system I tossed together for windows media center, and in my defense I have been working at the evil empire for some time and don't know a thing about linux.  

My main concern is installing without being able to recover and get back into windows.

---

### Post by overdrank on 2008-02-08
> **Shrek X said:**
> So, I just wanted to see if I am missing anything from one of the lunux gods. .  


I have a desktop computer, has two physical hard drives, one is a RAID drive, the other IDE.  I have my stuff backed up, and I want to load ubuntu on the RAID drive, vista is on the IDE already (both are internal to the system).  


I have run the liveCD and it works great, looks happy, etc.

Is there anything I should watch for before I install?  Anything I am missing?  Will the live CD handle leaving the windows partition alone and be able to boot to whichever I choose?  

Sorry if this is a very rudimentary question, and no specific hardware information,:its a system I tossed together for windows media center, and in my defense I have been working at the evil empire for some time and don't know a thing about linux.  

My main concern is installing without being able to recover and get back into windows.

HI and welcome you may look at these raid links
[https://help.ubuntu.com/community/FakeRaidHowto#head-02740b764cae6f0bf06802280321d1bbdb01b039](https://help.ubuntu.com/community/FakeRaidHowto#head-02740b764cae6f0bf06802280321d1bbdb01b039)
[https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)

---

### Post by Shrek X on 2008-02-08
Thanks, I will read them before I begin.  I will add that the drive I want to install on isnt a RAID virtual drive, but a physical drive with a RAID controller (as I said, I just tossed the system together).  


BTW, I have to tip my hat to you people who have invested your time and knowledge not only in the software itself, but in the community your building.  MS and the other big boys could learn a LOT.

---

### Post by macogw on 2008-02-08
Check that your RAID controller works with Ubuntu.  Seeing "RAID" in the post gave me an automatic little "watch out" flag going off in my head.

If the Ubuntu install doesn't work, your Windows shouldn't be hosed (unless you install to the wrong disk--don't do that).  The worst that could happen while installing is that you overwrite the MBR on the wrong drive, and then Windows won't boot (in which case, use your Windows CD to boot, go to the repair console, and type "fixmbr").  Make sure you look at the last page before you finish the install.  The "advanced" button lets you mark which disk gets GRUB.  Make sure it's the one that has Ubuntu.  I'd suggest setting that disk as the first disk on your motherboard (in the BIOS) and then installing it (that'd make it hd0, by the way), so that you'll get GRUB coming up and it'll let you boot Ubuntu directly and should automatically chainlink to Windows' ntldr for you.  If you keep Windows as the first disk, make sure GRUB is on the second (hd1), but you might have to do some work to make the Windows ntldr chainlink to GRUB so you can boot Ubuntu.

---

### Post by Shrek X on 2008-02-08
> **macogw said:**
> Check that your RAID controller works with Ubuntu.  Seeing "RAID" in the post gave me an automatic little "watch out" flag going off in my head.

If the Ubuntu install doesn't work, your Windows shouldn't be hosed (unless you install to the wrong disk--don't do that).  The worst that could happen while installing is that you overwrite the MBR on the wrong drive, and then Windows won't boot (in which case, use your Windows CD to boot, go to the repair console, and type "fixmbr").  Make sure you look at the last page before you finish the install.  The "advanced" button lets you mark which disk gets GRUB.  Make sure it's the one that has Ubuntu.  I'd suggest setting that disk as the first disk on your motherboard (in the BIOS) and then installing it (that'd make it hd0, by the way), so that you'll get GRUB coming up and it'll let you boot Ubuntu directly and should automatically chainlink to Windows' ntldr for you.  If you keep Windows as the first disk, make sure GRUB is on the second (hd1), but you might have to do some work to make the Windows ntldr chainlink to GRUB so you can boot Ubuntu.

GREAT advice!  

So using the live CD, and setting it up that way, ubuntu has an equivalent of a boot.ini which will give me a selection of which OS to boot into?

and one more question if I may, should I format the drive I want to install on before I install? (currently NTFS).  

Thanks again

---

### Post by macogw on 2008-02-08
Uh, I guess.  Boot.ini is a config file, right?  The config file for the GRUB menu is in /boot/grub/menu.lst (or will be, once installed).  GRUB itself will be on the MBR.  The first stage of it loads from the MBR, then that looks at the partition it's set to look at, and finds the /boot/grub/menu.lst so it can display the menu that says something like:
Ubuntu <kernel>
Ubuntu <kernel> (recovery mode)
-- Other Operating Systems --
Windows Vista

If you want to make Vista boot first, you can edit /boot/grub/menu.lst from inside Ubuntu by using ```
gksu gedit /boot/grub/menu.lst
```
then count like this:
```

0 Ubuntu normal
1 Ubuntu recover
2 --Other OSes--  (yeah that counts as a line *shrug*)
3 Windows
```
and set the number next to the word "default" (around 15 lines down) to whatever option you want it to go with.  Then scroll down to around 125 lines down (or do ctrl+f and search for updatedefault) and change the value of updatedefaultentry to true so that when you get a kernel update (when the very center of Ubuntu gets updated to fix security vulnerabilites, fix drivers, or because you're doing an upgrade) and Windows gets shoved down, the number you set up top will automatically change.

If you want the menu that lets you pick between Ubuntu and Windows to automatically be displayed, put a # before the word "hiddenmenu" If you leave it uncommented it'll just say "loading GRUB... press Esc to enter menu" when you boot.  

How long it displays the "press Esc..." message or how long it displays the menu on boot before automatically loading the default is determined by the line that says "timeout"  The number next to it is how many seconds you want those things to last.

---

### Post by ispy on 2008-02-08
The linux native filesystem is ext3, and it cannot work on an ntfs. you can read and write, but not install. you will need to format the ntfs drive. there are programs available for you to be able to see and access all the files on your windows drive from within Ubuntu.

welcome :)

edit: sorry if I'm unclear. your Linux drive must be formatted, not windows. you can leave windows untouched. and as for the bootloader, I think macogw said it best.

---

### Post by Shrek X on 2008-02-08
wow... I am very impressed with the responses and level of knowledge shared here.

---

### Post by Shrek X on 2008-02-08
> **ispy said:**
> The linux native filesystem is ext3, and it cannot work on an ntfs. you can read and write, but not install. you will need to format the ntfs drive. there are programs available for you to be able to see and access all the files on your windows drive from within Ubuntu.

welcome :)

edit: sorry if I'm unclear. your Linux drive must be formatted, not windows. you can leave windows untouched. and as for the bootloader, I think macogw said it best.

The HD its going onto is free, will it format the drive itself even thought it is NTFS?  or do i need to low level?

As I am going to dedicate the full drive to ubuntu, should I just disconnect the windows drive and let it go (that will effectively guarantee nothing happens to the windows drive), and if I do that can I get back to state where the two see one another at boot?

sorry if these are dumb questions

---

### Post by ispy on 2008-02-08
the drive Linux is going on to will have to be formatted to ext3. you might also want to set up a swap partition, just in case. your windows can be left as NTFS. the live CD installer has a utility to set it to use the best options on one disk (ie: formatting it, setting a swap partition, etc) automatically. just be careful, one wrong click and it's all over.

just to be clear. the drive will be formatted/must be formatted.

edit: yes, you can just disconnect the drive or disable it temporarily in your bios.

---

### Post by Shrek X on 2008-02-08
> **ispy said:**
> the drive Linux is going on to will have to be formatted to ext3. you might also want to set up a swap partition, just in case. your windows can be left as NTFS. the live CD installer has a utility to set it to use the best options on one disk (ie: formatting it, setting a swap partition, etc) automatically. just be careful, one wrong click and it's all over.

just to be clear. the drive will be formatted/must be formatted.
[B]
edit: yes, you can just disconnect the drive or disable it temporarily in your bios[/B].

and then come back and setup the duel boot?

---

### Post by ispy on 2008-02-08
grub (Ubuntu's default bootloader) might give you an error after starting back up, in which case you can use a program called supergrub which will edit the entries easily for you. or you can add the entry yourself by editing the file on your system from a Live CD. there are lots of forums herre that deal with how to add the entry so that Grub can read it.

supergrub can be written to a CD, so you can load directly to it in case of emergencies. it's saved my life a couple times.

edit: or you can just load ubuntu without plugging windows back in so you don't have to go through a live CD. then plug windows HDD in, mount it, edit your grub file, and reboot. if it doesn't recognize Windows as an OS after that, SuperGrub is really useful for that kind of thing.

---

### Post by Shrek X on 2008-02-08
> **ispy said:**
> grub (Ubuntu's default bootloader) might give you an error after starting back up, in which case you can use a program called supergrub which will edit the entries easily for you. or you can add the entry yourself by editing the file on your system from a Live CD. there are lots of forums herre that deal with how to add the entry so that Grub can read it.

supergrub can be written to a CD, so you can load directly to it in case of emergencies. it's saved my life a couple times.

Impressive...  


so, I have pulled the IDE drive, and am now diving into the deep end :)  I can always reconfigure the hardware after the fact and reinstall if tihs method doesnt work, just want to make sure my mediacenter stays working with the Xbox :)  

another question, would it be possible to load the Vista session in VM ware after everything is running and I have the ubuntu session up?  

Sorry if the questions keep popping up in my mind and you guys are amazing.

---

### Post by ispy on 2008-02-08
I'm not knowledgeable with Virtual Machines enough to help you out there. good luck with Ubuntu though!

---

### Post by Shrek X on 2008-02-08
Ill let you know how that works when I get there. 


Thank you all VERY much, I must say, even thought there is some things that need to be tightened up here and there, this thing ROCKS! And the community just adds another 2 points to that

---

### Post by Shrek X on 2008-02-09
took the jump, currently managing my dual boot with the bios, but Ill figure that out later.  

Everything else went like clockwork, got all the fancy graphics happening including the cube thing and all that goo, got my vista HD to mount so I can see the files on there (didnt get it going the other way though, gonna have to figure that one out).

Anyhow  

I just wanted to post up again and say thank you to everyone who helped, in this thread and in the form where I got other information... even thought they may not read it :)

---

