---
title: "PowerBook G4 15&quot; won't boot live CD 7.10 - white screen or black screen"
date: 2007-10-28
forum: Apple PPC Users
---

### Post by kidkangaroo on 2007-10-28
Hey guys - so I thought I'd try Gibbon on my Mac.  Downloaded the PPC version and burned the CD.  When I slot it in and boot holding down "c" it comes up with the screen to hit enter or try some alternate boot options.  No matter which option I try I get one of three results -  White screen of death, black screen with a flashing curser (the CDROM just spins down), or a command prompt (can't recall what the prompt says - but I can get it when I use one of the options after I TAB at the boot menu.)

So here's my spec:

PowerBook G4 15" 1.67Ghz
Machine Model: PowerBook5,6
768 MB ram
Matshita DVD-R  (came with it)

I tried the same CD on my wife's PowerBook G4 15" 1.33Ghz and it worked just fine.  

Any ideas what is wrong with my model?  I have looked all over the forums and seems nobody has had this problem yet...  thanks in advance for your help!

:confused:

---

### Post by BladeMelbourne on 2007-10-28
Have you tried the Gutsy 'Alternate ISO'?
How does your wife's hardware differ from your own? (hehe, no, this is actually a serious question).

The dingo stole my baby!

---

### Post by bodek on 2007-10-28
Hi, just finished downloading Gutsy and had similar problem on PowerBook G4 15" 1.33GHz. What made is load was to use the 'live video=ofonly' option. Also the 'live-nosplash-powerpc' seems to work well.
Otherwise the screen goes just grey and then white and the CD stops.

Maybe it is a problem with video card?
My pbook has ATI Mobility Radeon 9600 M10 rv350

---

### Post by NateTheMacGuy on 2007-10-28
I am running into a similar problem.  When I start up from CD, I either get a black screen with a white, flashing cursor or a white screen with a grey, flashing cursor.  A short time after this, the CD drive spins down.  I have only tried a couple of alternate modes (I can't remember which ones, but "live video=ofonly" was one), but they all ended with the same black or white screen.

I also tried an old 6.10 Live CD that I have only used in live mode, and it worked just fine like it has in the past.  There is an error message that has always popped up on the splash screen just after the black screen with the white "X" disappears.  I don't remember what it said, but 6.10 runs fine when I just ignore the message and click "OK".  I haven't tried the 7.10 Alternate Install disc, because I think it would be more frustration than I wnat to go through.

My hardware specifications are: G4 iMac with 800 MHz processor, 512 MB of RAM, and a 15" display.  Any help within the next day or so would be much appreciated, as I don't have school tomorrow.  Thanks in advance.
__________

Here is some info about my graphics card from System Profiler.  This is all of the info from the Graphics/Displays section.
NVIDIA GeForce2 MX:

  Chipset Model:	GeForce2 MX
  Type:	Display
  Bus:	AGP
  VRAM (Total):	32 MB
  Vendor:	nVIDIA (0x10de)
  Device ID:	0x0110
  Revision ID:	0x00b2
  ROM Revision:	1057.008.4
  Displays:
iMac:
  Display Type:	LCD
  Resolution:	1024 x 768
  Depth:	32-bit Color
  Built-In:	Yes
  Core Image:	Not Supported
  Main Display:	Yes
  Mirror:	Off
  Online:	Yes
  Quartz Extreme:	Supported

---

### Post by SycloneMedia on 2007-10-29
There are a slew of related/un-related problems with either your video driver package and/or your splash at boot and it's been discussed in another thread.

Take a look here if you're having the same problem, I summed up the solution to the black screen due to splash problems:
[http://ubuntuforums.org/showpost.php?p=3614279&postcount=58](http://ubuntuforums.org/showpost.php?p=3614279&postcount=58)

If your problem is with your video package, then I suggest you guys read through that whole thread (link will be in top right corner of that page) since there are good solutions to either problem...

Hope that helps you guys out...

---

### Post by NateTheMacGuy on 2007-10-29
Thanks for your help, but I'm kind of confused.  I assume that I am supposed to follow the steps outlined below the three stars.  At the command where I am to select my boot type, I typed "live-nosplash-powerpc video=ofonly".  Then, I got some computer text that I didn't understand followed by a prompt saying "(initramfs)".  I'm not sure what this means, but I tried entering "live-nosplash-powerpc video=ofonly" again and it spit out a line saying "/bin/sh: live-nosplash-powerpc: not found" and then gave me the same prompt again.  I then tried just hitting enter, which just gave me the prompt again.

Also, in step 1, when you mention getting it "installed", are you refering to getting the CD to load or installing Ubuntu on the internal hard drive.  I really, really don't want to do this, because I need my OS X stuff to work.

-Thanks
Nathan

---

### Post by pxwpxw on 2007-10-29
> **NateTheMacGuy said:**
> Thanks for your help, but I'm kind of confused.  I assume that I am supposed to follow the steps outlined below the three stars.  At the command where I am to select my boot type, I typed "live-nosplash-powerpc video=ofonly".  Then, I got some computer text that I didn't understand followed by a prompt saying "(initramfs)".  I'm not sure what this means, but I tried entering "live-nosplash-powerpc video=ofonly" again and it spit out a line saying "/bin/sh: live-nosplash-powerpc: not found" and then gave me the same prompt again.  I then tried just hitting enter, which just gave me the prompt again.

Also, in step 1, when you mention getting it "installed", are you refering to getting the CD to load or installing Ubuntu on the internal hard drive.  I really, really don't want to do this, because I need my OS X stuff to work.

-Thanks
Nathan
If you just want to use the Live (Desktop) 710 CD -
 Repeat what you did, until you get to the (initramfs) prompt -
 Then try typing these commands -
```

(initramfs) modprobe ide_disk
(initramfs) modprobe ide_cd
(initramfs) exit

```
Then see if that goes on from there to bring up the desktop, it might work.
This was noted by **lunalot** and is another problem with loading  modules for disk drives. 
The steps after that are only relevant for an installed system.

---

### Post by razinjap on 2007-10-30
As many of you here, I've been through nothing but troubles since I installed 7.10 on Aluminum PowerBook G4. :confused:
I guess, Linux is the OS that makes you think, dig and explore, but sometimes it gets really frustrating, especially for those of us who are not experienced enough.  
Let me conclude at least for myself that, imho, 7.10 is not yet ready for "right-out-of-the-box" use on PPCs. 
The question is, if this situation is going to be changed soon? Is there any work going on making 7.10 with all its nice and useful stuff really painless OS for PPC users? 
Off for changing my info from Ubuntu 7.10 user back to Ubuntu 7.04. :(

---

### Post by xevix on 2007-11-04
I have a Powerbook G4 12" that had the same problem with Kubuntu 7.10, and after combining solutions, I've gotten it to work.

1.) At yaboot:

live-nosplash-ppc video=ofonly break=top

2.) At busybox:

modprobe ide_core
modprobe ide_disk
modprobe ide_cd
exit

*NOTE: the busybox commands have to be entered all the first time around before `exit` or else it will fail and you'll have to reboot to try again.

3.) The cd will start to load.  Be patient, it took me 3-5 minutes for the full boot, but it booted.

---

### Post by caladan1810 on 2007-11-05
Hi everyone,

I have tried the following 

1.) At yaboot:

live-nosplash-ppc video=ofonly 

2.) At busybox:

modprobe ide_core
modprobe ide_disk
modprobe ide_cd
exit

when I type exit it keeps me in busybox prompt and will not exit. I'm at a total loss at trying to get the 
Ubuntu 7.10 Live CD to actually boot into the 'Live CD' Environment. Previous CD's have had no problems at all. This is the first time I have had any issues with an Ubuntu Live CD. I'm hoping someone can tell what I'm doing wrong. If anything.

thanking you in advance for your help

Cal :)

---

### Post by scott.huang on 2007-11-05
Hello everyone, 

I too am having problems with this.  I'm using an old powerbook g4 machine.  I followed cal's instructions and that actually got me all the way through the install!  Unfortunately, when I rebooted things went wrong.  I was shown the boot manager, then I was asked which os to use, and then I get a the black screen with blinking cursor.  (by the way, during installation I opted to wipe the drive clean, so there's no dual boot stuff going on). 

Something I thought was interesting, after I downloaded the iso file (ubuntu-7.10-desktop-powerpc.iso) I tried to mount it in os x and it gave me an error saying the disk image was probably damaged.  After I click the "don't open" option it says "The following disk images failed to mount" ubuntu-7.10-desktop-powerpc.iso and the reason it states is "no mountable file systems".   perhaps the image on the server is corrupted?  I tried downloading it a couple of times.  Does this happen for anyone else?

scott

---

### Post by scott.huang on 2007-11-05
Hello everyone, 

I too am having problems with this.  I'm using an old powerbook g4 machine.  I followed xevix's instructions and that actually got me all the way through the install!  Unfortunately, when I rebooted things went wrong.  I was shown the boot manager, then I was asked which os to use, and then I get a the black screen with blinking cursor.  (by the way, during installation I opted to wipe the drive clean, so there's no dual boot stuff going on). 

Something I thought was interesting, after I downloaded the iso file (ubuntu-7.10-desktop-powerpc.iso) I tried to mount it in os x and it gave me an error saying the disk image was probably damaged.  After I click the "don't open" option it says "The following disk images failed to mount" ubuntu-7.10-desktop-powerpc.iso and the reason it states is "no mountable file systems".   perhaps the image on the server is corrupted?  I tried downloading it a couple of times.  Does this happen for anyone else?

scott

---

### Post by eyeballer786 on 2007-11-05
I too have had this problem. When i did the (initramfs) commands, it still did not work. It said it could not find them. I'd love it if someone who created this knew of this, and rewrote it to make it stable.

---

### Post by smackswell on 2007-11-05
I believe i saw it on the Ubuntu PPC wiki. Anyways the recommendation was to upgrade via feisty with the update manager. 

once gutsy was installed i had to do 

modprobe ide_core

to get it to actually run. I DO NOT RECOMMEND UPGRADING TO GUTSY AT THIS TIME! Here's why:

While I was running it my compy was hot. HOT. I mean melty hot. I'm using the last version of the TiBook and was frankly concerned it was gonna fry, Additionally, I updated the initcramfs before i restarted and gutsy would not restart. I ended up just erasing it and going back to feisty.

There are a lot of issues with this release that i think are best left to those who really know what they're doing. If you're a n00b as I am, play with feisty for now, =;

---

### Post by richard_der on 2007-11-06
I would echo these sentiments. Having upgraded 7.04 to 7.10 the system fails to boot. This has been tried on 3 different G4s just in case there was any hardware peculiarities. 7.04 worked without problems. IMHO 7.10 ppc should be WITHDRAWN until such time as it has been thoroughly tested.

---

### Post by shields on 2008-03-21
Wow -- I have looked and looked for this answer.  Thanks, xevix.

I am using Ubuntu 7.10 and made the entered the following.  (It's just slightly different)

Insert the cd and hold down the C key until you hear it booting from the CD.

> 1.) At boot:

live-nosplash-powerpc video=ofonly break=top

2.) At busybox:

modprobe ide_core
modprobe ide_disk
modprobe ide_cd
exit


But the most helpful part of your post was this.
> 
3.) The cd will start to load. Be patient, it took me 3-5 minutes for the full boot, but it booted.
My impatience was getting the better of me.  It seemed to take more like 10 minutes -- during which there would be long periods of inactivity with the CD.

Thanks.

---

### Post by stream303 on 2008-03-22
> **smackswell said:**
> to get it to actually run. I DO NOT RECOMMEND UPGRADING TO GUTSY AT THIS TIME! Here's why:

While I was running it my compy was hot. HOT. I mean melty hot.

That's the time to take a look and see if your cpu is getting hogged by some process.  In the case of my iBook running Gutsy, when I ran top in a terminal, I saw that Network Manager was hogging the cpu and everything was running hot, not to mention a little slow. :)

I had to disable Network Manager, and everything was fine.  NM only had this problem on my iBook.

One of the first things I do after an install is fire up top, or bettery yet, download HTOP and use that in a terminal to see if there are any hungry processes that need taming. :)

---

