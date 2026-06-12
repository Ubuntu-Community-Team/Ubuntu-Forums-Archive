---
title: "Using WinGrub on 2 HDD system, how to point to the Ubuntu installation?"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by ccclairee on 2007-08-19
I installed WinGrub with the guide at [http://users.bigpond.net.au/hermanzone/p9/html](http://users.bigpond.net.au/hermanzone/p9/html)

Now when I boot, if I select "Start Grub", there is only one option in Grub; Windows at [hd0, 0]. When I select this, a diagnostic type deal comes up?

My Linux partition is at hd0, 0. Windows is at hd1, 1
 I've noticed that in WinGrub under the "default" profile there is "Windows at [hd0, 0]", do I need to edit this? How do I point it to my linux installation?

---

### Post by wolfen69 on 2007-08-19
the easier way would have been to install each OS on its own.(with the other drive physically unplugged) then choose which OS to boot in BIOS. most mobos now come with a quick boot option(F12, etc.) that will enable you to choose which drive to boot from without actually going into the bios.  ive done this on several machines and works great. grub isnt needed when 2 OS's are on different drives.

---

### Post by Duck2006 on 2007-08-19
You have to edit the menu table to point the loader to where the root partition is for ubuntu

root (hd0,0)
chainload +1

---

### Post by ccclairee on 2007-08-19
I did install each OS on its own HDD, I'm not given an option on which OS to boot in BIOS. Boots straight to windows. How do I solve this?

To Duck2006 - That is what is there by default.

---

### Post by Duck2006 on 2007-08-19
boot up the live CD and post the output of

sudo fdisk -l

---

### Post by ccclairee on 2007-08-20
I don't know how to post it here, I don't have internet access from the live CD and cannot write to my C:\ drive, and windows cannot read the ext3 filesystem if I save it there?

---

### Post by logos34 on 2007-08-20
> **ccclairee said:**
> I don't know how to post it here, I don't have internet access from the live CD and cannot write to my C:\ drive, and windows cannot read the ext3 filesystem if I save it there?

[FS-driver]("http://www.fs-driver.org/download.html") will give you read+write support for linux ext2/3.

You actually can write/save to windows partition from live cd if you can install ntfs-3g (just loads into the RAM for that session).  But you need internet for that, so you'll have to use fs-driver from windows side

---

### Post by logos34 on 2007-08-20
By the way, I just installed wingrub using Herman's guide (followed it to the letter) and it worked perfectly.

Could you also post your boot.ini file (just type 'boot.ini' in windows explorer address bar)

---

### Post by ccclairee on 2007-08-21
[IMG]http://i215.photobucket.com/albums/cc69/ccclaireeee/IMG_7752.jpg?t=1187673076[/IMG]

took a picture.

also, bios.
```

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\GRLDR="Start Grub"

```

---

### Post by logos34 on 2007-08-21
> Now when I boot, if I select "Start Grub", there is only one option in Grub; Windows at [hd0, 0]. When I select this, a diagnostic type deal comes up?

My Linux partition is at hd0, 0. Windows is at hd1, 1
I've noticed that in WinGrub under the "default" profile there is "Windows at [hd0, 0]", do I need to edit this? How do I point it to my linux installation?

According to your fdisk and boot.ini, you are booting to sdb, the windows drive, and sdb2 is your C: drive, which is [rdisk(0)partition(2)] to boot.ini, and (hd0,1) to grub.  Confused yet?

Go back into windows and reconfigure WinGrub using Herman's page as a guide, so that "Start Grub" (grldr) is pointing to linux root partition on sda1, i.e. **(hd1,0)**.  Hopefully that'll fix it.

Why aren't you using Grub, if I may ask?

---

### Post by ccclairee on 2007-08-21
> **logos34 said:**
> According to your fdisk and boot.ini, you are booting to sdb, the windows drive, and sdb2 is your C: drive, which is [rdisk(0)partition(2)] to boot.ini, and (hd0,1) to grub.  Confused yet?

Go back into windows and reconfigure WinGrub using Herman's page as a guide, so that "Start Grub" (grldr) is pointing to linux root partition on sda1, i.e. **(hd1,0)**.  Hopefully that'll fix it.

Why aren't you using Grub, if I may ask?

I really can't figure out how to reconfigure WinGrub, is there a step-by-step sort of thing? Im sorry, I'm new and very confused.

I'm not using grub, simply because I don't know how to set it up.

---

### Post by Duck2006 on 2007-08-21
This sould help you set up grub

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by logos34 on 2007-08-21
> **ccclairee said:**
> I really can't figure out how to reconfigure WinGrub, is there a step-by-step sort of thing? Im sorry, I'm new and very confused.

I'm not using grub, simply because I don't know how to set it up.

I went back and fiddled with WinGrub and my impression is that the configuration setup is needlessly complicated.  (Until I tried out WinGrub I had grldr/grub4dos installed on my dual boot and it was super easy to set up.  But more on that later).  And there doesn't seem to be anything out there in terms of a step-by-step guide beyond the howto you used.

I'd recommend you use Grub to boot both OSs.  I'll try to keep it simple:

Boot up the live cd.  In a terminal type:

[B]sudo grub
find /boot/grub/stage1[/B]
(enter the output 'hdx,0' in the next command.  'x' will be 0 or 1)
**root (hdx,0)  **
**setup (hdx)**  --this installs grub to the MBR of the linux drive, /dev/sda)
**quit**

Reboot and enter the Bios setup.   Go to the **hard disk boot order **section (not to be confused with the device boot order) and set your linux drive, sda, FIRST. 

The Grub menu on sda should appear upon reboot.  Select the first ubuntu kernel and hit 'e' key to edit.  Hit 'e' again on the** 'root'** line and change it if necessary to **(hd0,0)**.  Hit 'enter' to save and 'b' to boot.  If that works, make the change permanent when you get into ubuntu by editing the corresponding root lines in menu.lst:

**gksudo gedit /boot/grub/menu.lst**

Change the 'groot' line and all the root lines in the 'automagic kernels' section to (hd0,0)
 
Your windows entry at the bottom should look like this:

> title		Windows XP
root		**(hd1,1)**
[B]map         (hd0) (hd1)
map         (hd1) (hd0)[/B]
savedefault
makeactive
chainloader	+1

(*More about this in the section '[Chainloading on a non-first hard disk]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")' at the link Duck2006 provided)

Then,

**gksudo gedit /boot/grub/device.map**

It should look like this:

> (hd0) /dev/sda
(hd1) /dev/sdb

Give that a shot and post back with the results.

---

### Post by ccclairee on 2007-08-29
this worked. thank you very much. :)

---

### Post by logos34 on 2007-08-29
> **ccclairee said:**
> this worked. thank you very much. :)

Glad to hear it woked out.

---

