---
title: "Feisty under Parallels"
date: 2007-08-03
forum: Apple Intel Users
---

### Post by Peavey on 2007-08-03
Hello all.  I'm a complete noob to the Ubuntu world.  I had a live CD of Feisty Fawn and one of Dapper Drake that I plyaed around with, but I have recently decided to give it a go and see if how I like running Feisty Fawn directly from my hard drive.  And virtualization is much better than having to reboot constantly, so I downloaded the beta of both Parallels and VMware Fusion.  I used Bootcamp to make a new partition, booted from the Live CD and then reformated the Bootcamp partition and installed Ubuntu.  It boots just fine on its own, but when I try to start it through Parallels I get this problem:

[IMG]http://web.mac.com/chrisjniles/iWeb/Our_Series_Of_Tubes/Images/Picture%202.png[/IMG]

Now, I am going to give Fusion a try, but it is late and I have to be at class in a little over six hours.  So, my question is how do I get the kernel to load so I can boot using Parallels?  I want to give both programs a shot and see how they compare, but I can't do that if I can't get Ubuntu to run under one of them.

Any and all help would be appreciated.

---

### Post by cyberdork33 on 2007-08-03
well as far as I have seen, nobody has really gotten this working very well... Although it looks like you have made a bit of progress.

You are at a grub commandline. you should be able to specify the root device,  a kernel line, an initrc line, etc (as is normally found in your menu.lst file). after loading a kernel, you can then use the boot command to finish booting. See this site for available commands:
[http://www.gnu.org/software/grub/manual/html_node/Command_002dline-and-menu-entry-commands.html](http://www.gnu.org/software/grub/manual/html_node/Command_002dline-and-menu-entry-commands.html)

I am thinking that if you had directed grub to be install to the ubuntu partition instead of the MBR (change the default) you might have gotten a normal grub screen at this point. I may have to do some experimenting with this. In fact, it might be easier to do that, instead of messing with the above any. you can actually install grub from the grub commandline:
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html)
Pay special attention to the section that says "If you want to put GRUB into the boot sector of a partition instead of putting it in the MBR, specify the partition into which you want to install GRUB" and the command following. you need to specify the partition that you installed ubuntu to. I would assume that it is (hd0,2) as it starts counting at zero, so that 0=efi, 1=osx, 2=ubuntu

How did you setup parallels to get to this point? I may want to play with this a bit.

---

### Post by Peavey on 2007-08-03
Well, the first thing I did was to use Bootcamp to partition the drive, and then I followed [The MacBook Ubuntu Wiki]("https://help.ubuntu.com/community/MacBook") to install Feisty from a Live CD that I had.  After I confirmed that my installation was working and got the WiFi working, I rebooted into OS X, installed Parallels and tried to boot the "Windows" partition (since I used Bootcamp to make the partition, this is what the new partition is called) changing the settings to tell Parallels that it was an Ubuntu distro of Linux that I was trying to run and not some flavor of Windows.  I didn't change any of the other default settings.  And, when I look at how my HD is partitioned in Disk Utility in OS X, there is the OS X partition and then the / for Ubuntu is disk0s3 and the swap is disk0s4.  So, I will try loading the kernel from hd0,3 first.

And just to clarify, I really am a complete noob when it comes to Linux or even just Ubuntu.  I have minimal experience using the Terminal in OS X, and it has almost always been little things like file browsing or copying and pasting commands from tutorials I have found online.  In fact, if it werent' for the MacBook Ubuntu Wiki, I wouldn't have even gotten the WiFi working.

I'll take a look at those two links you posted and get back to you if anything works

---

### Post by cyberdork33 on 2007-08-03
> **Peavey said:**
> And, when I look at how my HD is partitioned in Disk Utility in OS X, there is the OS X partition and then the / for Ubuntu is disk0s3 and the swap is disk0s4.  So, I will try loading the kernel from hd0,3 first.

it will be (hd0,2) I am positive. OSX counts like this: 
1=EFI, 2=OSX, 3=Bootcamp, 4=swap
Grub on the other hand starts at 0
0=EFI, 1=OSX, 2=Bootcamp, 3=swap

I have a custom partitioning, so I can't choose to use the bootcamp partition. This is good though, sounds like we are getting somewhere.

BTW, it wouldn't matter if the WiFi was working or not, as in parallels, it is seen as completely different hardware.

---

### Post by Peavey on 2007-08-03
Okay, I installed grub to the Ubuntu partition, but when I try to load the kernel I get this error:

Error 1: Filname must be either an absolute pathname or a blocklist

I realize I must sound like a complete newcomer to this.  What do I type to specify the pathname?

---

### Post by cyberdork33 on 2007-08-03
> **Peavey said:**
> Okay, I installed grub to the Ubuntu partition, but when I try to load the kernel I get this error:

Error 1: Filname must be either an absolute pathname or a blocklist

I realize I must sound like a complete newcomer to this.  What do I type to specify the pathname?
try this, don't type the '>'
first need to specify the root:
```
> root (hd0,2)
```then the kernel:
```
> kernel (hd0,2)/vmlinuz root=/dev/sda3
```then
```
> initrd (hd0,2)/initrd.img
```finally
```
> boot
```
you shouldn't be seeing that commandline when starting up, it should boot the latest kernel installed, like when you boot natively. I am halfway inclined to wipe everything just to try this... cause I think you are onto something.

---

### Post by Peavey on 2007-08-04
Okay, so it turns out that partition 0 is the boot partition.  I installed grub again, and then followed the directions you posted using partition 0 instead of partition 2.  I had to rewrite to boot directions so that it looked for the kernel in partition 0 as well.

Anywho, it works, but all I get is the command line.  No GUI.  I can log in, and I can do everything you would do via the command line, but the desktop won't come up.  I'm going to do some google-ing to see what I can find to bring up the GUI.

Thanks for all of your help.

---

### Post by cyberdork33 on 2007-08-04
> **Peavey said:**
> Okay, so it turns out that partition 0 is the boot partition.  I installed grub again, and then followed the directions you posted using partition 0 instead of partition 2.  I had to rewrite to boot directions so that it looked for the kernel in partition 0 as well.

Anywho, it works, but all I get is the command line.  No GUI.  I can log in, and I can do everything you would do via the command line, but the desktop won't come up.  I'm going to do some google-ing to see what I can find to bring up the GUI.

Thanks for all of your help.

sweet. Maybe it sees it as 0 since you installed grub to the partition.

to get X up, try running 
```
/etc/init.d/gdm start
```

I still don't know how you got it to work. I tried it today, and still could get it to let me use the 'bootcamp' partition. Maybe you could post the config files so that others can import it to parallels. Maybe I can figure out how it works too.

---

### Post by Peavey on 2007-08-04
Let me know which config files you mean and I'll be happy to post them.

Anywho, when I run the start command that you showed me, first off I have to use sudo, and second, it just displays the following:
[HTML]*Starting GNOME Display Manger...                     [ OK ][/HTML]

And then brings up a new prompt.

Where do I go from here?

---

### Post by cyberdork33 on 2007-08-04
sorry yes sudo was required.

try hitting alt+F7 to switch to Xorg, and if there is nothing then alt+f1 or ctrl+alt+f1 should get you back.

the config file should be ~/Library/Parallels/NameOfVM/NameOfVM.pvs where NameOfVM is the Name you gave your virtual machine when setting everything up. There might be other stuff in there too, IDK.

---

### Post by russell.h on 2007-08-04
I just preordered vmware fusion (for $40, its 50% off if you order it by sometime today), and I've been playing with the beta. Feisty installed easily with the desktop CD (it booted the live CD and installed just as if it weren't in a vm). Windows XP works well too. After messing with Parallels I have to say that I highly recommend vmware fusion, at least from the standpoint of trying to run Ubuntu.

---

### Post by apswartz on 2007-08-04
I run Feisty on my MacBookPro. I didn't use bootcamp. I created an expandable virtual drive in Parallels and installed to that. I haven't encountered any problems. But, I do wish the Parallels team would spend a little more time developing a tools package for Linux like they have for Windows.

---

### Post by Peavey on 2007-08-05
Yeah, I couldn't get Parallels to work using the Bootcamp partition under Parallels.  I haven't tried it using an expandable virtual drive in Parallels like apswartz did, but it is working great under VMware Fusion so I think I'm just going to stick with that.

Sorry Cyberdork, but I forgot that you wanted the config file, and unfortunately I already deleted the Bootcamp partition (which took some doing.  Since it was no longer formatted for windows Bootcamp no longer recognized the Bootcamp partition.  At all.  I had to use the Ubuntu LiveCD to reformat it and then Bootcamp would recognize it and let me reunite my hard drive).

---

### Post by cyberdork33 on 2007-08-05
> **Peavey said:**
> Yeah, I couldn't get Parallels to work using the Bootcamp partition under Parallels.  I haven't tried it using an expandable virtual drive in Parallels like apswartz did, but it is working great under VMware Fusion so I think I'm just going to stick with that.

Sorry Cyberdork, but I forgot that you wanted the config file, and unfortunately I already deleted the Bootcamp partition (which took some doing.  Since it was no longer formatted for windows Bootcamp no longer recognized the Bootcamp partition.  At all.  I had to use the Ubuntu LiveCD to reformat it and then Bootcamp would recognize it and let me reunite my hard drive).

Ah ok cool. VMWare is a better option IMO anyway!

---

