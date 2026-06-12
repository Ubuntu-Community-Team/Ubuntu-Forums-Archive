---
title: "Can't install ubuntu"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by oblivioncth on 2008-03-30
My father wants to dual boot Ubuntu with Windows XP but he is having some trouble.
When he boots from the CD he gets to the menu and selects start or install Ubuntu like anyone would, and when he does it brings up the loading Linux kernel thing (still good),then show the Ubuntu loading thing but then. Instead of loading Ubuntu it brings up some weird thing that I have never seen before (see pictures), says something about initramfs or somthing. Also when he picks any option at the menu, when it shows the Ubuntu logo (when it is loading with that orange bar) it says failed allocate mem... (some other stuff).

Please help. :confused:

---

### Post by collinp on 2008-03-30
What is the specs of your computer because when i tried to install 7.10 i got that error because my computer did not have enough Ram at the time?

---

### Post by Duck2006 on 2008-03-30
What are the system are you trying to install on?
Did you burn it at X4 or the lowest speed you can on your burner?

---

### Post by oblivioncth on 2008-03-30
Intel quad core 
Intel BX2 Motherboard
8800 GTS Video card (Nvidia)
Ausintech Prelude (Sound card)
CD/DVD drive = Samsung Super Write Master
Hard drive: Two, one SATA one IDE
2 gigs of ram

Burned and 4 X

---

### Post by collinp on 2008-03-30
I believe that you have a error with your disk. The easiest way to get a error-free disk is to order one free. See here: [https://shipit.ubuntu.com/login](https://shipit.ubuntu.com/login)

---

### Post by oblivioncth on 2008-03-30
I will try to burn a new disk and if that disk doesn't work I will order one with your link so thanks.

---

### Post by Duck2006 on 2008-03-30
Check the cd with MD5Sum to see that it is good.

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by Agrajag27 on 2008-03-30
This is the OP's father. I have checked 3 different CD's now and all check out. I've also tried installing the 8.04 beta in addition to the 7.10 release. All have failed the same way.

I don't quite understand what the trouble is. Is there any other way of installing it? I've tried safe mode as well with the same result. 

Is there some tool I can run to present a collected log of what the full errors are? The ones I see fly by so fast that you can't really learn much from them.

That's 3 different CD's created on two different systems and two different major versions of the OS.

What else is left?

---

### Post by Duck2006 on 2008-03-30
You can try a text base install.

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Tatty on 2008-03-30
The Live CD can sometimes get upset while booting.  Try burning an Alternative CD...

To get the alt. cd, go to download as usual but check the checkbox saying "Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer."

If it still fails to boot the next step would be to try booting a different distro (fedora maybe).

---

### Post by mgmiller on 2008-03-30
You could try installing from the alternate install CD.  That's the one that is used to install the server version of Ubuntu.  Once it's running, install the desktop package:
```
sudo apt-get install ubuntu-desktop
```

Then reboot.  You should have a graphical install.

---

### Post by Tatty on 2008-03-30
> **mgmiller said:**
> You could try installing from the alternate install CD.  That's the one that is used to install the server version of Ubuntu.  Once it's running, install the desktop package:
```
sudo apt-get install ubuntu-desktop
```

Then reboot.  You should have a graphical install.


Actually the Alternate installer is for the Desktop version.  It will install the system as a normal Ubuntu Desktop, but it is not a live cd and has a text-based installer instead of the GUI one which comes with the live cd.

:)

---

### Post by alzie on 2008-03-30
I did some searching and found a similar problem here: [http://ubuntuforums.org/showthread.php?t=587168](http://ubuntuforums.org/showthread.php?t=587168)

> 
I looked up what initramfs does here:[http://linuxdevices.com/articles/AT4017834659.html](http://linuxdevices.com/articles/AT4017834659.html)

Then I poked around with commands in the initramfs shell. I saw that the directory called 'cdrom' in the OS ubuntu install booted into was empty. So I figured that it wasn't finding the "root". So the next time I booted from the Live CD, I specified an additional boot option (by pressing F6 when the ubuntu install menu comes up; each item in the install menu has a different set of options. You want to add in the options line for the install option) root=/dev/cdrom and hit install.

Viola!

I am writing from my newly installed Ubuntu. Hope this helps someone.

I'm hoping this will help you

---

### Post by mgmiller on 2008-03-30
> **Tatty said:**
> Actually the Alternate installer is for the Desktop version.  It will install the system as a normal Ubuntu Desktop, but it is not a live cd and has a text-based installer instead of the GUI one which comes with the live cd.

:)

Shows how long it's been since I had to do that.  :lolflag:

That is how it used to work in 6.06 or some such, can't remember how far back.  Thanks for the heads up.

---

### Post by Tatty on 2008-03-30
> **mgmiller said:**
> Shows how long it's been since I had to do that.  :lolflag:

That is how it used to work in 6.06 or some such, can't remember how far back.  Thanks for the heads up.

Ah technological things always completely changeswhen you take your eye off them for a second dont they. lol.  :)

---

### Post by Agrajag27 on 2008-03-31
Getting a bit further now.

The Alternative version installed. GRUB said it spotted XP Pro and installed with that in mind and said it was time to reboot.

I did and XP booted flawlessly with no mention of Ubuntu what-so-ever!

One thing during install that seemed off is that I was never asked about creating a "home" directory. I saw "Swap", I saw "Root" but not sure the third one ever got created.

---

### Post by Agrajag27 on 2008-03-31
Quick update. Partition Magic (Windows app) reports that I have two partitions. A very small SWAP partition and another larger partition. Both are listed as LINUX EXT3 so it appears that part went well but why isn't it triggering GRUB to provide a boot option to reach it?

Here's the breakdown of drives:

Disk 1
Other F: NTFS 92GB Primary
Local Disk  Linux EXT3 24GB Primary (Active)
* Extended 1GB
SWAPSPACE2 (*.) Linux Swap 1GB Logical

Disk 2
Main C: NTFS Primary (Active)
* Extended 186GB Primary
Games D: 150GB Logical
Technical E: 36GB Logical

---

