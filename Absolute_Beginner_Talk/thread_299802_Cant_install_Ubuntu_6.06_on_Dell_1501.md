---
title: "Cant install Ubuntu 6.06 on Dell 1501"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by redDEADresolve on 2006-11-14
I just bought a new AMD powered Dell Laptop (1501). It has a sepron 3500+ processor, ATI 1150 graphic card, 512 MB of 533 DDR2 RAM, 60gig SATA hard drive. (I know I gotta get more RAM but I wasn't gonna pay Dell to put it in)

I can't get Ubuntu 6.06 to run the live CD/install. I get to the Ubuntu splash screen (pictured) and can't start or install Ubuntu or start Ubuntu in safe graphic mode. I just get a blask screen. I left it for 15 minutes and nothing changed. I can load into windows fine.

I then loaded in Edgy 6.10 and loaded in fine until I got to the install screen, edgy could not "see" my hard drive. This might be the same problem but every piece of info helps right?

Any Help? I want to use Dapper Drake 6.06

---

### Post by redDEADresolve on 2006-11-14
this is the picture of my PC

---

### Post by ReaderRat on 2006-11-14
Are you sure you have a good disc? To check this, from the CD menu, run the option to check the checksums on the disc. May be a bad copy...
You have plenty of RAM to install Dapper or Edgy.

---

### Post by redDEADresolve on 2006-11-14
> **ReaderRat said:**
> Are you sure you have a good disc? To check this, from the CD menu, run the option to check the checksums on the disc. May be a bad copy...
You have plenty of RAM to install Dapper or Edgy.

yes i forgot to mention i tried both my burned copy that worked on my desktop install and the one i recieved from canonical

---

### Post by ReaderRat on 2006-11-14
Have you tried using 'Safe Graphics Mode' (On the CD menu)? And you might look this over...   [**ATI Mobility Drivers**](http://www2.ati.com/drivers/linux/linux_8.8.25.html)

---

### Post by redDEADresolve on 2006-11-14
Neither:
start or install Ubuntu 
start Ubuntu in safe graphic mode

work, I just the black screen of death.

my hardware works, RAM test was ok, hard drive loads, processor is fine.
no CD defects

I do not want to use windows tonight, I'm a spolied Ubuntu user.
Help me fellow ubuntu geeks, you're my only hope.

---

### Post by DannyG on 2006-11-14
Have you tried the Alternate Install CD?

---

### Post by moshuptrail on 2006-11-14
Well, thinking out loud...
1. Since Dapper is pretty tried and true, we should probably assume a hardware incompatibility.  (I guess I'm also assuming you've got some pretty new hardware in that machine - maybe something that Ubuntu hasn't seen before)
2. When you run the live CD it needs to use your CPU and your video.  Not much else.  Right?  So it must be failing on one of those.
3. From your description, it sounds like the CD boots, and runs a little bit, but stops at some point.  Maybe if we can identifiy what point, it will lead to the incompatibility.

Can you give more detail?

---

### Post by redDEADresolve on 2006-11-14
> **moshuptrail said:**
> Well, thinking out loud...
1. Since Dapper is pretty tried and true, we should probably assume a hardware incompatibility.  (I guess I'm also assuming you've got some pretty new hardware in that machine - maybe something that Ubuntu hasn't seen before)
2. When you run the live CD it needs to use your CPU and your video.  Not much else.  Right?  So it must be failing on one of those.
3. From your description, it sounds like the CD boots, and runs a little bit, but stops at some point.  Maybe if we can identifiy what point, it will lead to the incompatibility.

Can you give more detail?

Yeah, my machine came out Nov. 1st, Dell just shipped them this week. I guess I'm one of the first to get one.

CD does boot, and runs until after you select either: start or install Ubuntu -or- start Ubuntu in safe graphic mode, the screen goes black and nothin happens. The CD makes a sound and then goes dead. If you look at the pic I attached in my second post you'll see the last thing i see until my screen goes black.

Is the Alternate Install CD an option for me?

Thanks

---

### Post by moshuptrail on 2006-11-14
My first guess would be video.  In which case, you will be using Windows tonight.

Is the video in that machine a new flavor?

---

### Post by ReaderRat on 2006-11-14
Need other info....Dell model, Video card, laptop...?

---

### Post by redDEADresolve on 2006-11-14
I listed these in my first post, I clarified a little more but what do you want to know?

Dell AMD Laptop Model Number 1501

Mobile AMD Sempron  3500+ Processor (1.8GHz/512K)
ATI Radeon  Xpress 1150 256MB HyperMemory (integrated)
512 MB of 533 DDR2 RAM (1 Dimm)
60gb 5400 RPM SATA hard drive
DVD+/-RW with Dual Layer DVD+R write capacity
Dell Wireless 1390 802.11g Mini Card (54Mbps)

---

### Post by ReaderRat on 2006-11-14
Sorry, didn't reread the first post...
[**ATI Mobility Drivers**](http://www2.ati.com/drivers/linux/linux_8.8.25.html)
Scroll down the page...

---

### Post by ReaderRat on 2006-11-14
I have tried to find your drivers for 20 minutes now....sorry, no luck. You may google on 'ATI Radeon XpressS 1150 AMD linux drivers' and give it a go.

---

### Post by paulajohnw on 2006-11-14
ANSWER HERE!!!!!  Works with ATI Graphics

This is a very common problem and guess what I HAVE THE ANSWER!!!!!!!

I pieced this together over the last couple of hours.

1.  At the 1st screen where it gives you all the options for installing, press "F6" (Options)

2.  delete "  splash --" from the boot options

3.  Choose option #1 "Start or Install"

4.  Looks like nothing is happening for a couple of mins.  Probably depends on ur PC

5.  XServer Fails, Skip all the reports and such

6.  You should now get a terminal window.  Type the following...  
  "sudo apt-get install xorg-driver-fglrx" <enter>
  "sudo aticonfig --initial" <enter>
  "sudo aticonfig --overlay-type=Xv" <enter> (notice that is Xv not xv x is caps)

7.  startx
8.  viola

---

### Post by redDEADresolve on 2006-11-14
> **paulajohnw said:**
> ANSWER HERE!!!!!  Works with ATI Graphics

This is a very common problem and guess what I HAVE THE ANSWER!!!!!!!

I pieced this together over the last couple of hours.

1.  At the 1st screen where it gives you all the options for installing, press "F6" (Options)

2.  delete "  splash --" from the boot options

3.  Choose option #1 "Start or Install"

4.  Looks like nothing is happening for a couple of mins.  Probably depends on ur PC

5.  XServer Fails, Skip all the reports and such

6.  You should now get a terminal window.  Type the following...  
  "sudo apt-get install xorg-driver-fglrx" <enter>
  "sudo aticonfig --initial" <enter>
  "sudo aticonfig --overlay-type=Xv" <enter> (notice that is Xv not xv x is caps)

7.  startx
8.  viola

i tried your method, i still get the black screen, i get this:

Uncopressing Linux... ok botting kernel
MP BIOS bug 8254 Timer not connected to IO-APIC

Any idea what this is?

---

### Post by redDEADresolve on 2006-11-15
still nothing anyone else got any ideas?

---

### Post by hades_6_6_6 on 2006-11-17
Same notebook, same problem :( 
Does someone have a solution?
I don't want to use windows any longer:evil:

---

### Post by hades_6_6_6 on 2006-11-18
have made some progress.
using following boot options (I don't no which one is really usefull):
noapic nolapic acpi=noirq

I've been able to start the dapper live CD:D , but then it is the same problem as with Edgy:
Hard disk not detected ](*,) :(

---

### Post by pyros on 2006-11-19
hmmm. looking for a solution too. the system chipset is listed as ATI RS485M / SB600.
the sb600 is the southbridge, and is responsible for controlling the sata.

---

### Post by hades_6_6_6 on 2006-11-19
> **pyros said:**
> the sb600 is the southbridge, and is responsible for controlling the sata.

Can it have something to do with the errors displayed at boot?:
```
[17179572:456000] PCI: Cannot allocate resource region 7 of bridge 000:00:5.0
[17179572:456000] PCI: Cannot allocate resource region 8 of bridge 000:00:5.0
```

---

### Post by pyros on 2006-11-19
no clue, I'm assuming that the hard disk not being detected is due to a problem utilizing the sb600 chip. the video is a radeon x300 so that should be easy enough to get working. the sata seems to be teh problem.

---

### Post by zekayi on 2006-11-22
> **redDEADresolve said:**
> i tried your method, i still get the black screen, i get this:

Uncopressing Linux... ok botting kernel
MP BIOS bug 8254 Timer not connected to IO-APIC

Any idea what this is?

I had the same problem (Bios bug) on my Inspiron 1501 (with turion x2). It was because I used accidently the intel iso image that I used successfully on my PC running with Intel. 
With the 6.06 amd64 image, I could boot from cd, start the installation and made it up to the point where the hdd needs to be selected. But there was no selection available.
Now working on this problem...

---

### Post by hades_6_6_6 on 2006-11-23
Thank you for replying, but this issue is already fixed. Look [here]("http://ubuntuforums.org/showthread.php?p=1786658").
This thread can be marked as Resolved.

---

### Post by BlueN1nja on 2006-12-05
> **hades_6_6_6 said:**
> have made some progress.
using following boot options (I don't no which one is really usefull):
noapic nolapic acpi=noirq

I've been able to start the dapper live CD:D , but then it is the same problem as with Edgy:
Hard disk not detected ](*,) :(

I'm having the same problem. Dapper Live CD AMD64, boots fine but I cannot get it to recognize the HDD. Tried acpi=force irqpoll in the boot options, but this doesn't help either.

Thought I'd reply to this thread rather than the other one as I'm having issues with Dapper, not Edgy.

---

### Post by rbprogrammer on 2006-12-05
> **redDEADresolve said:**
> this is the picture of my PC

i dont know if i can help, but i have a inspiron E1505 with the widescreen.  i cant tell in your picture, but i think you probably have the widescreen as well.  unlike you, i was able to log into the live cd and do an install. but for the graphics to work correctly i had to install the package 915resolution.  now, i think like someone else in this post that you have a graphics problem, it may be that your new computer has some hardware that ubuntu needs software for. may even be the 915resolution package.  unfortunately i dont know how to help you, but that package fixed my graphic problems.

---

### Post by M_N_M74 on 2006-12-17
I'm having trouble installing Dapper Drake on my Dell 1501 Inspiron notebook with a toshiba mk8034gsx hard drive and an amd 64 athalon processor.  The live cd works fine, but when you attempt to install it freezes at step 5.  I have tried both the pci-nomsi and aci=force irqpoll and still have the same error.  Anyone have any other suggestions?  Also am unable to format the hard drive...is this a related problem?

---

### Post by bodhi.zazen on 2006-12-17
> **M_N_M74 said:**
> I'm having trouble installing Dapper Drake on my Dell 1501 Inspiron notebook with a toshiba mk8034gsx hard drive and an amd 64 athalon processor.  The live cd works fine, but when you attempt to install it freezes at step 5.  I have tried both the pci-nomsi and aci=force irqpoll and still have the same error.  Anyone have any other suggestions?  Also am unable to format the hard drive...is this a related problem?

I am not sure if I have any solution to any problem here.

But, I just finished will a Dell laptop....

What I had to do first was update the BIOS. This likely does not apply here as your boxes are newer then mine.

M_N_M74: I had a similar problem. I could boot the Live desktop CD just fine, but it would not install or partition. Just kept locking up.

Tried the alternate CD, no luck. The install started and failed at 85%

What I did was to install fluxbuntu, which went without a hitch. I then installed ubuntu-desktop.

Fluxbuntu:

	[Main page](http://fluxbuntu.org/)

	[forums](http://community.fluxbuntu.org/)

[Download fluxbuntu-nbuild1-rev2-desktop-i386.iso](http://modzer0.cs.uaf.edu/~hardwarehank/fluxbuntu/rev2/fluxbuntu-nbuild1-rev2-desktop-i386.iso)

	MD5SUM  :  > c054428c46a1b5ffaab4295bc7db3c9b  fluxbuntu-nbuild1-rev2-desktop-i386.iso

The only problem I had was with X, I had to manually configure the monitor.

HTH

---

### Post by M_N_M74 on 2006-12-18
The same problem occurs with Fluxbuntu as well.  Thank you for the attempt, anyone else have any ideas?

---

### Post by redDEADresolve on 2007-01-22
[http://ubuntu1501.blogspot.com/](http://ubuntu1501.blogspot.com/)

use edgy, the dapper work around is getting mixed reviews

---

### Post by M_N_M74 on 2007-01-25
Edgy is 6.10 right?

Will your visual walk thru work for a dual boot system?

Need a dual boot until everything works on Ubuntu.

Thanks
M&M

---

### Post by redDEADresolve on 2007-01-25
yes it will work. follow all the steps except partition your hard drive so that you don't delete your windows partition. if you don't know what this means. the install will walk you through it. is so easy you have to be retarded to mess it up. if you still have trouble google or search the forums for info for dual booting.

---

### Post by M_N_M74 on 2007-01-26
Thanks, I'll give it a try

---

### Post by Ronirvol on 2007-01-27
Using 6.06, the pci=nomsi did not work with my Dell 1501, but it looks ok using 6.10.   The live CD seems to work.  I can't complete the install however, because I can't figure out the partitioning.  It looks like I need to manually add 2 primary partitions, one ext3 and one swap.  I would like to keep the installed Windows XP, and my Dell 1501 already has stuff in 3 primary partitions.  Gparted says it will not let me add  a 5th primary partition.  Is the only solution to delete one of the Dell partitions to be able to create the two new ones that I need?  Any suggestions would be appreciated.

---

### Post by M_N_M74 on 2007-01-29
I attempted to set up my own partitions and then ended up installing Edgy over my windows partition anyway.  That was loads of fun.

Anyway the second time around I chose the automatic partitions and everything worked fine.

I would try the use the biggest continious chunk of memory option for partitions.

---

### Post by Cobikegeek on 2007-01-29
To get around the 4 primary partition limit, you need to create an extended partition.  You can then create several (up to 16, I think) logical partitions.  For example, you can have 3 primary partitions and one extended that supports several logical partitions.  All the logical partitions must occupy a continuous block of disk space.   The extended partition is named like other partitions sda1, sda2.... but isn't really a storage partition except to store other logical parititions. Linux does not care if it is on a logical or primary partition.  Good luck.

---

### Post by Ronirvol on 2007-01-29
Thanks Cobikegeek!   That works.  Before running the install I used gparted to create an extened partition.  Inside of it I was able to create the two partitions, ext3 and swap, that I needed.  When I stepped through the install I selected manual install, and it even recognized and selected the partitions that I had previously created.  My install is now working.  I would also like to thank redDead for the install instructions on the blog.

---

