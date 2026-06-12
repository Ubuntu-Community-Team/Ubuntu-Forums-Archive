---
title: "How long should a straight install take?"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by ablot on 2007-06-13
Hi,

I have decided to install ubuntu 7.04 on my laptop - and get rid of windows completely.

How long should it take? At this time it has taken 40 minutes and I am left with a blank install screen ... and the CD has stopped doing its blinking thing.

I ask this question because I tried yesterday and after three hours everything just stopped ... and I was left with ... Windows!! Ubuntu did not do anything. I have since burned another CD, and I am now waiting to see what happens. 

... Actually the install has just started up again ... but is it going to do anything ... or am I going to have a repeat of yesterday?

---

### Post by drs305 on 2007-06-13
It shouldn't take that long. On my installs there are only a couple of long (10-20 minute) delays - actually installing the system and then updating the files. Other than that, there isn't a significant delay between installation sections.

Are you using an ISO disk? That is, can you see the files on the installation CD? 

Here is a good link to help install ubuntu. The link is about ISO images but the index on the left side will help you install ubuntu:

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by ablot on 2007-06-13
... Just to add that I have seen your install guide.

The main difference here is that you say that if I double click the install button I will then begin to receive a number of windows starting with the WELCOME window and my choice of langauge ... when do I get this window?

It has now been coming up to an hour ... I still have a blank INSTALL window ... the CD is chuntering away ... shouldn't I get the WELCOME info soon?

---

### Post by Outrunner on 2007-06-13
There's definitely something wrong. Do you have 256 MB of RAM(or is it less?)?

---

### Post by ablot on 2007-06-13
Hello drs305 - thanks for getting back to me.

Yes it is an ISO disk ... I'll have a look at psycocats ... thanks.

Presumably, I can just turn off the computer?

---

### Post by ablot on 2007-06-13
Hi Outrunner ... yes 256 of RAM

---

### Post by skymera on 2007-06-13
hmmm
mine took few mins =S
whats the min requrirements>?
256ram? DDR2

---

### Post by drs305 on 2007-06-13
*
You might tell us what version you are trying to install. It sounds like a CD problem. Are you familiar with a utility which checks the integrity of the CD called md5sum. You run the program and it looks at the CD to make sure everything is correct. When it finishes, it produces a code. You compare that code to the published one and if they match you can be pretty sure you have a good CD. 

You can do a search for the program - there are versions for windows and linux.

The md5sum codes for feisty 7.04 are:

50f3655fbcbdba9746d4b05ad8705b0b *ubuntu-7.04-alternate-amd64.iso
ff0cc7c9ed5157f0ff8c0f2213973f49 *ubuntu-7.04-alternate-i386.iso
a2b159599b69cea51371eee1ec5feda6 *ubuntu-7.04-desktop-amd64.iso
e296e3468358789904097fc8df29609a *ubuntu-7.04-desktop-i386.iso

* edited to reflect md5sum program name

---

### Post by ablot on 2007-06-13
I produced an ISO of 7.04 ... checked it with mdsum (the comparisons were the same) ... and burned it to a CD ... I tried InfraRecorder but that did not work ... so I used Deep Burner - which did.

---

### Post by ablot on 2007-06-13
Sorry skymera ... I don't understand your question ... my laptop (which is a new one) has 256 of ram ... what's DDR2 ?

---

### Post by bigken on 2007-06-13
if your getting rid of windows use the gparted liveCD to format your hdd 1st then try running the live disc installer

---

### Post by ablot on 2007-06-13
... OOOPS!

Actually the laptop has 224 of RAM!!

Is that significant?

---

### Post by bigken on 2007-06-13
its does have 256 mb your graphics card is using 32mb of it

---

### Post by ablot on 2007-06-13
gparted live CD? Whats that? Where do I get it from? What does it do?

Help Obe One Kinobe your my only help!!

---

### Post by bigken on 2007-06-13
I would also consider this do you have the restore discs if not there will be a hidden partition on your hdd do not delete or format this as you may decide to go back to windows at some time

---

### Post by bigken on 2007-06-13
> **ablot said:**
> gparted live CD? Whats that? Where do I get it from? What does it do?

Help Obe One Kinobe your my only help!!


its in my signature

its a partition editor quite easy to use

---

### Post by ablot on 2007-06-13
... But why do I need a partition editor? Can't I just install ubuntu onto the laptop?

... Restore discs? No I don't think there are any of those.

---

### Post by zer0x41 on 2007-06-13
> **ablot said:**
> ... But why do I need a partition editor? Can't I just install ubuntu onto the laptop?

... Restore discs? No I don't think there are any of those.

Before the installation, in partition manager, you choose to format and install all the disk automatically, or you choose manual?

---

### Post by vanadium on 2007-06-13
An install of Edgy took me about 30 minutes, and then another 30-40 minutes to update (I installed in April, just before the advent of Feisty).

The install CD has an option to check the CD: run that to check your CD. Indeed it might be a problem with the CD, but also with your CD drive.

Then there is also the option to run the alternate install CD. This one relies on simple text screens.

256 MBytes should be fine. 128 is probably the minimum, but before I knew that, I installed Ubuntu on a 64 K system and I succeeded. I could not boot the live CD the first time, but after a few times, I succeeded with booting and with the install. If I were to do that again, I would use an alternate CD.

You should probably post hardware specs here, such as the graphics card you use etc. That might ring a bell with some people.

---

### Post by xpod on 2007-06-13
The very first machine i installed Ubuntu on had 224MB of RAM and like you i could load the Ubuntu desktop up ok  but as soon as i tried to install the thing it would just freeze.
Using "safe graphics mode" from the start screen on the live cd solved it for me but failing that you could always try the "alternate cd".

Better still would be Xubuntu:p

---

### Post by Tomosaur on 2007-06-13
When you first boot the LiveCD, you will have a number of options. The most important two are 'Start / Install Ubuntu', and 'Check CD Integrity'. If you're having problems with the LiveCD (which apparently, you are), choose the Check CD Integrity option. This should hopefully tell you if something is wrong, but if the problem is severe enough, then even this may malfunction. The best option, I find, is to just scrap the CD if you have problems with it. Burn another one, but use the slowest possible burning speed to minimise the risk of a fault.

When you click the install icon on the LiveCD desktop, a window should pop up which will guide you through the install process, asking various questions. Eventually you will be asked about partitioning, but for now, just focus on getting the install program to pop up in the first place.

A Linux installation typically needs a minimum of two partitions. If you plan to only use Linux on your laptop, then the automatic install should be fine for you. If, however, you want to use both Windows and Ubuntu on your laptop, then you will need to choose one of the other options, and may have to set up the partitions yourself.

---

### Post by smartsaah on 2007-06-13
Ideally a installation should not be taking more than 20mins.

After following the thread, I suggest you to burn the downloaded image file of the Ubuntu OS (i.e an .iso file) through Nero or Power ISO software.

When the burning is done, re insert the CD and you are supposed to get a CD explorer containing basic infos about Ubuntu..and other associated softwares like Firefox etc..

When you get to see the intro portion, you can be sure that the CD is burnt properly with all the required stuff inside it.

After that boot you PC while leaving the CD in the tray. This will lead you to a menu screen with various options such as Start and install Ubuntu  and so on.

Then you can select the Start and install Ubuntu which will lead you to the installing process.:(

---

### Post by bigken on 2007-06-13
Ok do as others have said reburn the ISO I would use [this]("http://isorecorder.alexfeinman.com/isorecorder.htm") to burn it in windows 

reboot with new cd 

select install on the desktop

at the partition select manual 

for your partitions I would go this way 

10 gig /  system

512mb swap twice your ram 

what ever is left   /home  

if you see a fat partition this your ghost image to restore the windows

---

### Post by lazyart on 2007-06-13
He's got less than 256 mb of RAM since video is stealing 32 megs.

Therefore he should use the alternate CD to install.  The LiveCD will do exactly what it is doing now-- hang when trying to install.

---

### Post by ajskhan on 2007-06-13
***_I had that exact same problem - use the alternate CD. _***

---

### Post by drs305 on 2007-06-13
> **lazyart said:**
> He's got less than 256 mb of RAM since video is stealing 32 megs.

Therefore he should use the alternate CD to install.  The LiveCD will do exactly what it is doing now-- hang when trying to install.

I agree. I had an old laptop with about the same memory setup and the alternate CD installed ubuntu (Edgy at the time) without any problems.

---

### Post by bigken on 2007-06-13
I managed to install ubuntu on a laptop with shared memory (256mb-32mb) without any problems and it was only a pentium III 800mhz cpu :D

---

### Post by lazyart on 2007-06-13
> **bigken said:**
> I managed to install ubuntu on a laptop with shared memory (256mb-32mb) without any problems and it was only a pentium III 800mhz cpu :D

If might work if the planets are aligned properly but I would never recommend trying.  For a skeptic who is giving it a try it just something they can use to say "Linux isn't ready for the desktop...."

---

### Post by ablot on 2007-06-13
... So let me get this straight ... using the live CD is causing it to hang ... right?

I have just tried again only using another computer to burn the CD ... I m5sum'd it then I get the ubuntu facility to check the integrity of the CD (which it said was OK) ... I then opened up from the disk the ubuntu desktop ... then I duoble clicked the INSTALL button on the left ... all that was 30 odd minutes ago ... and the CD is happily chuntering away and the screen has remained the lovely brown colours ... but no welcome window - yet.

That doesn't look too promising ... so Lazyart, you reckon I should try the alternative CD which is a text based installer ... OK I'll have a go.

---

### Post by stalkingwolf on 2007-06-13
I have had to go to the install option under (I think) system>admin to get install to kick off.  But remember
everything you do under the live cd is slow/er and determined by the amount of ram you have.

---

### Post by ablot on 2007-06-13
Ok ... I ve started to install using the SAFE mode ... and it appears to be working - a bit slow ... but I'm getting the different windows with questions being asked.

I'm now on the partition page  ... I have three choices but I do not knowwhat they mean:
1. /dev/hda2 
2. /de/hda1
3. free space

I presume this is the windows alocation.
Do I press the NEW PARTITION TABLE to delete these or do I do something else?

---

### Post by ablot on 2007-06-13
Is there anyone out there who can point me to simple instructions (ie for non techno newbies) as to how I partition my laptop? I do not want a dual boot ... I want the whole computer to be ubuntu.

I think I have to press the NEW PARTITION TABLE button which then gives me the whole 40g as free space. I know that I double click on it to open up the CREATE PARTITION window.

I am going to follow the advice I got earlier: 10g for root; 512k for swap; the rest as free space 

... So I think the first one is primary and I use as ext3, mount point is '/'.
... the next will be Logical and I use as swap ... I dont know what mount point would be.
... Third will be Logical ... I dont know what I use as ... or what mount point.

Can any one help?

---

### Post by limelightos on 2007-06-13
don't put 512k for swap!

you want 512MB

---

### Post by resander on 2007-06-13
I also tried the liveCD graphical installer on a 256MB Pentium III.

It didn't work. After a few minutes the screen went blank. I abandoned after 90 minutes and tried again using a CD burnt by InfraRecorder (it works!), but the result was the same.

I followed the advice to use alternate iso distribution and the installation completed in about an hour. 

I didn't know which partitioning method to use so I asked the forum and got many really useful responses. You may want to read these. Search on my username resander to get there quickly.

---

### Post by ablot on 2007-06-14
Thanks Resander ... your threads on partitioning reads well ... I'l be looking into it today.

... And thanks to all of you who have patiently guided my faultering steps along the path ubuntu ... I'll keep you all posted.

---

