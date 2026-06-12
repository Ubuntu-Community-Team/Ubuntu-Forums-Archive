---
title: "starting the virtual machine... 0%"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by gelmce on 2007-07-27
I am trying to install Windows-XP Home to a VM of VirtualBox v1.40.
Base OS is Ubuntu-7.04-desktop.
From Ubuntu default user GUI, Applications, System Tools, Innotek VirtualBox;
I clicked NEW, followed the dafaults, Windows-XP, 192 MB RAM (?),
8 MB video memory, 9.77 GB disk space.
I then clicked on START, selected CDROM install.
Now the install windows seems hung.
 The windows has been displaying:
starting the virtual machine... 0%
 for over 4 hours now.  

What could be wrong?

Regards, Chuck

---

### Post by Majorix on 2007-07-27
Are you sure XP supports 8mb video card? That seemed really low to me...

---

### Post by gelmce on 2007-07-27
Dear Majorix:

Are you sure XP supports 8mb video card? That seemed really low to me...

  I selected OS from menu, Windows-XP.
If more than 8 MB video card is needed for Windows-XP, then
Virtual Box should default to a larger MB for video card.
Bios is reserving 256 MB for video memory.
I do not recall  VirtualBox ->  NEW VM  asking me how much video memory to reserve!

?

Chuck

---

### Post by jingo811 on 2007-07-27
I used Automatix2 to install VirtualBox on my Feisty. In case you didn't install it like that.  Doing it manually or by following Ubuntugeeks tutorial involves too many error factors.

If things freeze in VirtualBox then restart the simulation by pressing ( Right-Ctrl + R ).  It shouldn't be that slow but it froze on me once also, just restart the VBox.  Also I assigned 512 MB to it on my 1 Gig machine.  But I've ran Ubuntu and Win XP on VBox before on 192 Meg however you should assign as much RAM as you can afford approx 60-70% of what you have.


.......Why do you want to have Win XP under Ubuntu?

---

### Post by gelmce on 2007-07-27
I do not know how to use Automatix2.
I installed from [http://www.virtualbox.org](http://www.virtualbox.org) and UnserManual.pdf .

I see no change while pressing Right-Control + R.

Are you suggesting that I run Ubuntu under Windows-XP ?

---

### Post by Majorix on 2007-07-27
Don't use a VM.. Your best bet is a PHYSICAL machine.

---

### Post by AndyCooll on 2007-07-27
> **Majorix said:**
> Don't use a VM.. Your best bet is a PHYSICAL machine.

I strongly disagree. Using a VM is a perfectly acceptable way of accessing XP, especially if the only reason you need XP is for just one app or something similar. In such cases dual-booting is a royal pain-in-the-***.

To the OP. The settings you mention are default ones and it would be worth starting again and increasing them if you have the RAM. For instance, my box has 2GB RAM so I allocate up to 1GB for virtual machines. And as has been indicated, extra RAM for video might be worthwhile too (it's in the "General" tab). 

:cool:

---

### Post by gelmce on 2007-07-27
Sorry, everyone. I thought I was posting in VirtualBox-Forum.

Regards, Chuck

---

### Post by michwill on 2007-07-27
I'm having the exact same problem.  It's just sitting at 0%.  Is this a permissions issue of some sort?

---

### Post by jingo811 on 2007-07-28
Are you using Ubuntu Feisty Fawn?  In that case just follow those 6 steps in order to install Automatix2.
[http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_on_.28K.2CX.29Ubuntu_7.04_i386.2CAMD64_.28Feisty.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_on_.28K.2CX.29Ubuntu_7.04_i386.2CAMD64_.28Feisty.29)
If not then check out the overview page, you'll want to install with **Apt. that's number 3** method.
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

Installing VBox by following the instructions on their official page involves too many error factors.  Installing VirtualBox with Automatix2 is just a simple click with no need for manual configurations.  It just works right away!

> Are you suggesting that I run Ubuntu under Windows-XP ?
You still haven't answered my question yet.
.......Why do you want to have Win XP under Ubuntu?

And NO I'm not suggesting anything since you didn't answer my question.  What I'm saying is that I've run simulations with Ubuntu at one time and Win XP at another time under VBox from my Ubuntu Feisty Fawn machine.  They were just simulations for taking screenshots.
When I want to run Win XP games and programs I use my Dual Boot partition.  Running Win XP during your Ubuntu sessions makes everything slow even when you assign it 512 MB RAM you can't even listen to mp3 without laginess.

---

### Post by sdowney717 on 2007-07-31
I just installed virtualbox and installed xp pro and it is working fine.
you have to be in the user group which I could only figure out by letting anyone in but so what.
do this by typing in 'sudo chmod 666 /dev/vboxdrv'

Downloaded the feisty .deb from virtualbox.org
Installed it with package manager
Start it from terminal by typing 'VirtualBox'

OOPS, just to show you how crazy this was,
scott@scott-desktop:~$ VirtualBox
WARNING: You are not a member of the "vboxusers" group.  Please add yourself
         to this group before starting VirtualBox.

         You will not be able to start VMs until this problem is fixed.

scott@scott-desktop:~$ sudo adduser scott vboxusers
Password:
Adding user `scott' to group `vboxusers' ...
Done.

OOPS!, just who am I anyway?
scott@scott-desktop:~$ VirtualBox
WARNING: You are not a member of the "vboxusers" group.  Please add yourself
         to this group before starting VirtualBox.

         You will not be able to start VMs until this problem is fixed.

scott@scott-desktop:~$ sudo chown root.vboxusers /dev/net/tun
scott@scott-desktop:~$ sudo chmod 660 /dev/net/tun

scott@scott-desktop:~$ VirtualBox
WARNING: You are not a member of the "vboxusers" group.  Please add yourself
         to this group before starting VirtualBox.

         You will not be able to start VMs until this problem is fixed.


BUT IT IS WORKING NOW! Everyone now can get in that is fine with me on my home PC.

scott@scott-desktop:~$ sudo chmod 666 /dev/vboxdrv
scott@scott-desktop:~$ VirtualBox
Qt WARNING: X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Qt WARNING: Failed to open device
Qt WARNING: X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Qt WARNING: Failed to open device

---

### Post by gelmce on 2007-08-01
jingo811 asks:
"Why do you want to have Win XP under Ubuntu?"

 I want linux as my base O/S.
I have been using Slackware since ~1996.  I started with kernel 1.1.13, I think.
I was trying out Ubuntu because my brother started using it.
WinXP came with this new computer and I'd like to use it.
I use linux to archive,rip/burn music CDs and movies/TVSeries DVDs, BitTorrents, ...
Sometimes I like to play M$Windoze games while waiting for DVDs to compile and burn.
I find it easiest to print using Windows.

 I am concerned that this configuration might be slow because you said that
MP3s on your system are 'laging'.  The only thing that might allieve my concern
is if my system is much faster than your system and then I might not have the
'laging'.  My computer is an AMD64x2 5200, 2 GB RAM, 500 GB hard disk.

Do you think that I would have a 'laging' problem?

 Thanks for the Automatix2 install instructions.

 I just tried [k]qemu install instructions at
 https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo
and ran into a snag, so I'll probably give your install instructions a try soon.

Thanks, Chuck

---

### Post by gelmce on 2007-08-01
Hi, Jingo811:

Thanks.  I had a problem with the first and last steps(1 & 6).

Step 1 did not seem to append 
 deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
to the end of /etc/apt/sources.list.
 So I edited it manually.

Step 6 returns this error:
E: Couldn't find package automatix2

Steps 2-5 seemed to work OK.

"Are you using Ubuntu Feisty Fawn?"

I am using ubuntu-7.04-desktop-i386.iso . I have no idea how to tell what mood
the anumal is in nor what animal it is!
 uname -a returns ...kernel 2.6.20-16-generic...
 
 In that case just follow those 6 steps in order to install Automatix2.
[http://www.getautomatix.com/wiki/ind...4_.28Feisty.29](http://www.getautomatix.com/wiki/ind...4_.28Feisty.29)

Regards, Chuck

---

### Post by gelmce on 2007-08-01
I think I got automatix2 installed.
I loaded a link to the .deb file with Firefox.
This invoked GDebi and then it seemed that automatix2 was installed.

Now how do I use automatix2 to install VirtualBox ?

Regards, Chuck

---

### Post by gelmce on 2007-08-01
Re-installed VirtualBox using Automatix2.

I still have the same problem...

starting the virtual machine... 0%


:-|

Chuck

---

### Post by gelmce on 2007-08-02
I think I found 99% of my problems.

Instead of typing by hand and making my usual many dyslexic errors,
I have been "cut'n'pasting"  the commands shown in the various web pages
into script files.  I just found out that Ubuntu uses 'dash' instead of
standard 'bash'.  Geeesh!

  I still have the same error with Ubuntu/VirtualBox, though.
Even when typed by hand.

 However, I just got kqemu/qemu running by typing the suggested
command lines in by hand.  From now on I'll remember to put
#!/bin/bash
at the top of my Ubuntu shell scripts.  ;-)

Is this why I don't find any install scripts for Ubuntu applications?

Chuck

---

### Post by AndyCooll on 2007-08-04
Just as a side issue, you DON'T need to install Automatix to get VirtualBox. 

You simply go to the VirtualBox download section [here]("http://www.virtualbox.org/wiki/Downloads"). Then choose the version you want, probably Ubuntu 7.04 and the i386 version. It then downloads a deb which you can save to you home directory. Once its downloaded just double click on it and it will install.

You then add yourself to the vboxuser group (System > Administration > Users And Groups > Manage Groups) and away you go!

:cool:

---

### Post by jingo811 on 2007-08-07
yadda yadda yaddda.....

---

### Post by Tux Aubrey on 2007-08-07
Virtualbox 1.4 and qemu are both available in Feisty repositories. Why are people looking for install scripts and other sources?  I installed VBox via Synaptic, added myself to the Vboxusers group and was up and running in 10 minutes (but not for Windows, no, no, no - another Linux distro - I don't do windows.)

And I'd like to propose that we don't solve beginner problems by recommending Automatix. 

After reading [http://ubuntuforums.org/showthread.php?t=517202](http://ubuntuforums.org/showthread.php?t=517202) and [Matthew Garrett's technical review]("http://mjg59.livejournal.com/77440.html"), I think most people will be going cold turkey on Automatix.  Its really no longer required now that codec and video driver installs have been automated.  Everything else is in the repositories or available as a .deb package somewhere.

---

### Post by jingo811 on 2007-08-07
yeah even better like Commodor Tux above said :)

---

### Post by teutatis on 2007-08-24
as a small sidenote I have the same problem since i got my new HP notbook. 
on my old NB there was no problem. 

I've installed VBox in any thinkable way... and always the same problem: 

Vbox freeze in "starting the virtual machine... 0%"

---

### Post by anewguy on 2007-08-27
Just curious - have any of you having this problem tried using VMWare Server instead?  If so, did you get an error of some sort there as well?:)

---

