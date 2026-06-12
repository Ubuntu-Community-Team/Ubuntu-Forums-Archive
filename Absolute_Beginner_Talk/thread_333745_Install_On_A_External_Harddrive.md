---
title: "Install On A External Harddrive"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by wwjoeyd on 2007-01-07
how do i install ubuntu onto an external harddrive?
the reason why im not replacing windows is because it would void my warrenty

any help would be really appreciated :D

---

### Post by maniac_X on 2007-01-07
You may want to look at this thread. I'm sure there are more you can turn up with key word searches but this one seems like it would hit the top of the list.

[http://www.ubuntuforums.org/showthread.php?t=80811](http://www.ubuntuforums.org/showthread.php?t=80811)

.

---

### Post by wwjoeyd on 2007-01-07
thank you

---

### Post by wwjoeyd on 2007-01-08
i am very confused
i feel stupid


please help me
i have 80gig external

---

### Post by scj on 2007-01-08
The first question is, what hard drives does Ubuntu see when you try to install (something along the lines of /dev/...)

Do you know if your Hard drive is an IDE, SATA, etc.?  It's okay if you don't, but it may save some time.

---

### Post by wwjoeyd on 2007-01-08
it says its IDE HDD 

and i havent tried to install it yet because im not sure if it will replace windows

and where do i install it? when in windows or when i am running the ubuntu cd rom thing? 

thanks alot

---

### Post by scj on 2007-01-08
I assume you are using Ubuntu 6.10.  Now 6.10 has a really nice feature that allows you to boot (by default) to a "liveCD."  This liveCD allows you to test Ubuntu on your computer without actually installing anything.  To state it another way, it will not alter your hard drive.  So feel free to boot using the CD.

Once you're in the GUI, you'll see an icon that has "install" under it.  Just follow that until you get to the part about partitioning disk drives.  I'm not sure if you are new to Linux, but it uses a different method of labelling hard drives than Windows.  Windows uses (a: c: d: etc.) whereas Linux uses (/dev/hda aka primary master IDE /dev/hdb aka primary slave IDE) furthermore, there is a number after the last letter indicating the partition number on that IDE drive (so /dev/hda1 is the first partition on /dev/hda)

Now, how do you connect the external hard drive to the machine?

---

### Post by wwjoeyd on 2007-01-08
i have used the the cd rom to boot up ubuntu and not alter my pc


i connect my external hardrive through usb, it has 2 usb plugs but only one is required

---

### Post by scj on 2007-01-08
On the desktop does it have a "usbdrive" or something similar?  If so, could you click on it?  It should be /media/sda1 (but I could be mistaken)

And could you find a terminal (I think it is under Accessories (I am not using Ubuntu at the moment)) and type "df"

---

### Post by wwjoeyd on 2007-01-08
im in windows right now

i should go on the live cd to do this correct?

---

### Post by scj on 2007-01-08
Yes, go to the LiveCD.  All this being said, I think I've tried what you're about to do (and failed), so I'm not sure I can be of much more use.  In any event, the information I've told you to get should be useful if someone else wants to help you.

---

### Post by wwjoeyd on 2007-01-08
ok
their is a icon on the destop
its labled "FAT32"

i double click on it and thier are 2 folders named "recycled" and "system volume information"

and i did the terminal thing at typed df

and this is what came up
[http://i18.tinypic.com/4c1hu2q.png](http://i18.tinypic.com/4c1hu2q.png)

---

### Post by scj on 2007-01-08
Recycled and sys vol info are Windows stuff.  /dev/sdb1 is going to be what you want to install to.  Click on "install" and see if that option appears (eventually, you will see a /dev/..., stop there and report back), if not then I'm at a loss.

I'm not so sure about how your boot loader will work though...  Could someone fill me in on that?

---

### Post by wwjoeyd on 2007-01-08
ok
i got to the part "starting up partitoner"

and it just seems to stop @ 50% and not move 

is this normal?
[http://i11.tinypic.com/2mdijkl.png](http://i11.tinypic.com/2mdijkl.png)

---

### Post by wwjoeyd on 2007-01-08
you know what
forget this idea


thanks for your help alot for your help though

---

### Post by Seine on 2007-01-08
Good luck! Please come back when you're ready to try again.

Seine.

---

### Post by Frank Golden on 2007-01-08
> **scj said:**
> Recycled and sys vol info are Windows stuff.  /dev/sdb1 is going to be what you want to install to.  Click on "install" and see if that option appears (eventually, you will see a /dev/..., stop there and report back), if not then I'm at a loss.

I'm not so sure about how your boot loader will work though...  Could someone fill me in on that?
One big issue I can see is if you install the grub bootloader to the MBR of your XP drive
you have 1) altered your XP install. 2) you will need to probably need to have your external drive connected every time you boot up. 

Let me explain. If you allow the installer to place grub on the MBR of your main drive it will overwrite the XP MBR with what is called Stage 1 grub. Grub is the _GR_and _U_nified _B_ootloader. Stage 1 grub is a small file that points to a file on your Ubuntu Edgy drive called /boot/grub/menu.lst this file is located at the root (/) of your Ubuntu install.
It contains the info needed to boot Ubuntu (by default) and will boot Ubuntu or XP if the correct entries are there. You will be presented with a menu when you start your computer. If you drive is not plugged in when you start up stage 1 will point to a drive that
doesn't exist and you will get a grub error and no menu.

You can specify that grub stage 1 is installed to the MBR of your external drive.
This leaves your XP MBR alone.

However your computer BIOS needs to be able to boot USB external drives.
Most newer computers are able to do this.

My laptop for instance has a feature where if you press F12 during POST it will display a menu showing all the drives connected to my computer. 

see below for install info 

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

and see this great tutorial about dual booting (this is a large tutorial) but you really
should read before doing anything.

[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

---

### Post by scj on 2007-01-08
What if NTLDR was altered instead (to boot Ubuntu)?

---

### Post by Frank Golden on 2007-01-08
> **scj said:**
> What if NTLDR was altered instead (to boot Ubuntu)?
I think that qualify as altering XP which wwjoeyd doesn't want to do. Plus I don't know of a way to modify that file. Opening up with notepad shows gibberish. I wouldn't even think about altering this file.

---

