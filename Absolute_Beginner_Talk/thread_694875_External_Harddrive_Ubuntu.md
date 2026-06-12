---
title: "External Harddrive Ubuntu????"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Mitchlb on 2008-02-12
I just got a 500gb external harddrive. Can i install ubuntu on the harddrive?? So, rather than needing to dual boot, I can just plug in the harddrive whenever i wanted to use ubuntu??? If i can, how can i do this. If i can't, well, let me know. If at all possible, can i install ubuntu on 250gb rather than all 500??

---

### Post by skippi90 on 2008-02-12
I've been trying to do this all week and still no success. :(

---

### Post by Mitchlb on 2008-02-12
I haven't tried. I'm worried about screwing something up.  :)

---

### Post by oilchangeguy on 2008-02-12
> **Mitchlb said:**
> I just got a 500gb external harddrive. Can i install ubuntu on the harddrive?? So, rather than needing to dual boot, I can just plug in the harddrive whenever i wanted to use ubuntu??? If i can, how can i do this. If i can't, well, let me know. If at all possible, can i install ubuntu on 250gb rather than all 500??

sure you can install it on the external drive. and yes you can have it you only half on the 500gb. and to keep grub away from your other operating system(s) you'll need to set the bios to boot from the external drive first. and when it's not there the computer will boot as normal. and before you do anything like this, always, always back up your data. better safe than sorry.

---

### Post by Mitchlb on 2008-02-12
Do you know anyone who has been successfull?

---

### Post by Mitchlb on 2008-02-12
Maybee i shouldn't post this under absolute beginner talk.... What do you think i should post it under for best results??

---

### Post by brokenhachi on 2008-02-12
i dont see why this wouldnt work... just like booting from a CD. it would probably be slower than having ubuntu on your internal HDD because of the USB cable, but i dont see why it wouldnt work.

just choose "boot from external drive" on the boot menu i guess. 

oh and when you are installing you would probably have to find a way to tell ubuntu to install there and not to your internal drive.


said it before and ill say it again though, im not an expert. just a guess.

---

### Post by Mitchlb on 2008-02-12
Is there a chance it will mess with my hard drive?? I don't have much on it, and could easily take it off.

---

### Post by Mitchlb on 2008-02-12
There's a "boot from external drive" option????

---

### Post by Mitchlb on 2008-02-12
Oh. But that's when it's already loaded....

---

### Post by rzrgenesys187 on 2008-02-12
I know when I tried this once if the external hard drive wasn't connected it couldn't find grub and I couldn't boot into any operating system.  I would give you more info but that was my first linux experience and I had no idea what I was doing

---

### Post by Mitchlb on 2008-02-12
Concerning oilchangeguy's comment:

Thank you, but can you go into specifics???

---

### Post by Mitchlb on 2008-02-12
Has anyone actually done this???

---

### Post by Mykle87 on 2008-02-12
Yes I did it. I have a few questions though. Are you going to use this external ubuntu hard drive with the same computer or are you going to go from computer to computer to use it? I did the first one and ran into a grub error [here is my thread]("http://ubuntuforums.org/showthread.php?t=439411"). If you want to do the latter, then you should look for a persistant livecd install (basically letting your hard drive act like a livecd, loading drivers each time you boot up a machine while the persistance allows you to save data). First I guess you should make sure that your bios can boot usb devices.

---

### Post by Nirevus on 2008-02-12
Any computers you wished to use this on would need to support booting from a USB hard drive. This option can usually be found in your BIOS settings when you turn your computer on, it's certainly possible to install a persistent live system onto a USB stick and there are [many]("http://www.google.com/search?q=installing+ubuntu+on+a+livecd") [tutorials]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/") around for it.

When following this, you may run into an issue with GRUB errors, to fix this a [thread]("http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-21-when-trying-to-boot-xp-after-installing-ubuntu-7.04-on-seperate-hdd-552043/") on LinuxQuestions has the answer.

---

### Post by brokenhachi on 2008-02-12
the boot from external drive function should be available always, considering that your bios allows it. you'll have to check by booting into bios and looking.

it should say "press XX to go to bios/setup" when you turn on the comp. usually at  the bottom of the screen. (xx will be the key, for example F2 or ESC) 


though i dont recommend messing around in bios if you dont know what you are looking for. if you do, make sure you choose "exit without saving" when you are done.

---

### Post by roscal on 2008-02-12
I   tried installing gutsy on an external on the weekend.
I'm a noob bty.
I ended up with grub installed on my XP machine, and couldn't boot into windows, or the external drive with gusty installed on it, because grub didn't find the external to boot from.
The master boot record on the XP box ended up corrupted.
I had to use the XP disc to repair the mbr, in recovery mode.
I suppose I could have tried to salvage the XP machine, but 
I ended up just hosing windows entirely :) and installed gusty on the machine itself.
Not a big deal for me, I had all my data backed up nicely anyway
I was an idiot and not thinking, checked my bios after, and I have no option to boot from USB devices anyway.:guitar:
Anyway, we are now a windows free household here :)

Be careful.

---

### Post by ajgreeny on 2008-02-12
I think that during the installation the external disk will just show up in the list of available drives and you can chose to install to it just like it was another internal drive.  Just chose manual from the partitioning point of installation, then chose the  external disk, and remember to put grub on the external disk, not the MBR of your first internal hard disk, or you'll get a grub error when you boot.  You can do this if I remember by chosing the Advanced button when you get to that point, or alternatively, use the Alternate Install CD, text based, but still easy.

---

### Post by Mykle87 on 2008-02-12
> **ajgreeny said:**
> I think that during the installation the external disk will just show up in the list of available drives and you can chose to install to it just like it was another internal drive.  Just chose manual from the partitioning point of installation, then chose the  external disk, and remember to put grub on the external disk, not the MBR of your first internal hard disk, or you'll get a grub error when you boot.  You can do this if I remember by chosing the Advanced button when you get to that point, or alternatively, use the Alternate Install CD, text based, but still easy.

That is exactly how I did it. However, this will only allow you to use the external hard drive on the machine you use to install Ubuntu. A cooler way might be what Nirevus pointed out (especially if you use a lot of different computers or public computers).

---

### Post by jan quark on 2008-02-12
try this guide
my 2 cents

[http://www.pendrivelinux.com/2007/11/13/installing-ubuntu-to-a-usb-hard-drive/](http://www.pendrivelinux.com/2007/11/13/installing-ubuntu-to-a-usb-hard-drive/)

sorry if missed the point 
had a hard day

---

### Post by wrgarrett on 2008-02-12
> **jan quark said:**
> try this guide
my 2 cents

[http://www.pendrivelinux.com/2007/11/13/installing-ubuntu-to-a-usb-hard-drive/](http://www.pendrivelinux.com/2007/11/13/installing-ubuntu-to-a-usb-hard-drive/)

sorry if missed the point 
had a hard day

Excellent link except it will only work with a desktop where the internal drive(s) can be physically disconnected. I wonder if there is a work-around for laptops on dual-boot?

---

### Post by Mykle87 on 2008-02-12
> **wrgarrett said:**
> Excellent link except it will only work with a desktop where the internal drive(s) can be physically disconnected. I wonder if there is a work-around for laptops on dual-boot?

The work around is using the alternate cd. I installed it on my external usb hard drive without disconnecting my hard disks.

---

### Post by brokenhachi on 2008-02-13
> **wrgarrett said:**
> Excellent link except it will only work with a desktop where the internal drive(s) can be physically disconnected. I wonder if there is a work-around for laptops on dual-boot?


just pull your hard drive out. laptop hard drives, just like desktops can generally be removed.

---

### Post by Mitchlb on 2008-02-13
Regarding this comment: 

Yes I did it. I have a few questions though. Are you going to use this external ubuntu hard drive with the same computer or are you going to go from computer to computer to use it? I did the first one and ran into a grub error here is my thread. If you want to do the latter, then you should look for a persistant livecd install (basically letting your hard drive act like a livecd, loading drivers each time you boot up a machine while the persistance allows you to save data). First I guess you should make sure that your bios can boot usb devices.


I would like to turn it from computer to computer.... Can i download a presistant livecd install??? Would it let me use only half the HD space??

---

### Post by Mitchlb on 2008-02-13
Mykle87: How? How did you do it without removing the internal hardrives???

---

### Post by Mitchlb on 2008-02-13
It would function like Ubuntu normally would right?? Would it even be password protected??? And if i only did it on 250gb, when i plugged it into a computer using my usb port, would a "boot linux ubuntu 7.10" option come up? Because i also want to use it to transfer things from xp computer to xp computer.... Or would i, when i log into the computer itself, have to chose boot from external harddrive??? And if i didn't chose it, then i could transfer files????

---

### Post by Mitchlb on 2008-02-13
Is there no way, short of pulling my internal harddrive out, that i can install ubuntu 7.10 on 250gb of external hard drive??

---

### Post by raafaell on 2008-02-13
> **Mitchlb said:**
> Oh. But that's when it's already loaded....

Have you connect the external HD correctly?

---

### Post by raafaell on 2008-02-13
> **Mitchlb said:**
> Is there no way, short of pulling my internal harddrive out, that i can install ubuntu 7.10 on 250gb of external hard drive??

Yes, that's a good way to do it, take the old HD out of the box, and connect the new one correctly, and then make the install all over again, and hope for better results.
Good luck.

---

### Post by Mitchlb on 2008-02-13
Yhea, but i don't want to go though the trouble of taking a hard-drive out of my lap top.

---

### Post by Mitchlb on 2008-02-13
And the external hard drive is just usb. 500gb. Can i load ubuntu on it without taking out the internal harddrives??

---

### Post by cmo220 on 2008-02-13
I installed Ubuntu onto an external hard drive.  For me, it worked by putting grub on the main internal HDD.  It was kinda screwy how I came upon that.  I installed Ubuntu to the external drive and it just didn't work, booted right into windows.  Then I tried CentOS on the external drive.  That installed Grub onto my MBR and I could only boot into CentOS.  That pissed me off that their default would do that so I gave up on them and reinstalled Ubuntu.  When I did it this time it installed grub onto the MBR and had boot options for Ubuntu and Vista.  I'm assuming you could just install grub without going through the trouble of using another distribution.  With this option you can't use the external on any other computer than the one you installed from.  There might be a way, but I haven't figured it out yet.  Would be nice though.

---

### Post by Mykle87 on 2008-02-13
Ok Mitchlb. Well, when I installed Ubuntu on an external usb hard drive last year, all I did was download the alternate cd and install Ubuntu to the hard drive and put grub on that external hard drive. My Ubuntu install could only be used on my desktop which I used to install (as I pointed out earlier). You want to do something way cooler which is take your Ubuntu external hard drive with all your passwords and saved data and go from computer to computer and boot from it without affecting the computer you are using. This is called persistant liveusb. This guide looks like the one you want (it looks kinda difficult sorry)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
You can also look at this too
[https://help.ubuntu.com/community/LiveCDPersistence](https://help.ubuntu.com/community/LiveCDPersistence)
These drives show you how to partition the disk so you don't have to use the entire thing for Ubuntu.
If you have any more questions, feel free to ask. Good luck and let us know how it goes. This should be a fun little project.

---

### Post by brokenhachi on 2008-02-14
it should only take you 2 seconds to remove the drive from the laptop. flip it over and pull it out.

---

### Post by Mykle87 on 2008-02-14
> **brokenhachi said:**
> it should only take you 2 seconds to remove the drive from the laptop. flip it over and pull it out.

That is a terrible idea. Why do that when it is unnecessary?

---

### Post by Mykle87 on 2008-02-14
Check out this guide. Very concise. 
[http://ubuntuforums.org/showthread.php?t=647587](http://ubuntuforums.org/showthread.php?t=647587)

---

### Post by Mitchlb on 2008-03-21
I know it's been a little while, but i finally got it to work!! I have 250 working with ubuntu and i can switch it from computer to computer!
Thanks to mykle87 in particular!! I didn't even have to remove my hard drives! Thanks guys! 8)

---

### Post by Mykle87 on 2008-03-21
Awesome Mitchlb! I knew it wouldn't be difficult.

---

