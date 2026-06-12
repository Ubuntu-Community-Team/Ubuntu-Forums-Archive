---
title: "New Macbook Air: install issues ?"
date: 2008-10-22
forum: Apple Hardware Users
---

### Post by xavier10 on 2008-10-22
Hi everybody,

I am in the process of getting the new MacBook Air (128 Gb SSD version). This should be the ultimate travel machine for me: Linux for work, Mac OSX for managing/processing pictures (I use a lot of software not avail under Linux, and would not stand windows).

I am planning on installing Ubuntu on this machine. This will be my first Ubuntu install: I am currently a Gentoo user (I previously used a G4 and a thinkpad, and still use a MacBook Pro and a desktop all under gentoo), but want to try Ubuntu this time.
Is there a wiki dedicated to the MacBook Air ? I saw one for the MacBook, but there are quite a few differences in hardware: ethernet dongle, and SSD drive just to name two.

I have searched for a thread related to this new machine, but did not find any.

Am I correct in assuming that the only new issue compared to the old Macbook Air should be the Nvidia 9400 chipset ?
I did look into the thread about the new macbooks, and it seems this should not be too difficult to handle. Am I wrong ?

What about the SSD drive ? Is there any specific issue related to that ? (I did not see any mention of that in the Macbook Air thread I found in the archive).
Should I just use ext3 or do I need to consider another filesystem, dedicated to SSDs ? (for instance, to manager wear leveling) If yes, then what is best supported by Ubuntu ?

Any help, or pointer to an existing thread on any of these topics will be welcome.

---

### Post by kosumi68 on 2008-10-22
Regarding the new MacBook Air: new version, new problems.

For the MacBookAir1,1 there is this page:

[https://help.ubuntu.com/community/MacBook Air 1%2C1 and Intrepid](https://help.ubuntu.com/community/MacBook Air 1%2C1 and Intrepid)

The SSD is not really tested in any setup. Also, I have currently no working external monitor setup.

---

### Post by cyberdork33 on 2008-10-22
The SSD should look to the OS like any other internal storage device (hard drive).

Can you please verify the version number is MacBookAir2,1 ? It appears in System Profiler.

---

### Post by xavier10 on 2008-10-23
> **kosumi68 said:**
> Regarding the new MacBook Air: new version, new problems.

For the MacBookAir1,1 there is this page:

[https://help.ubuntu.com/community/MacBook Air 1%2C1 and Intrepid](https://help.ubuntu.com/community/MacBook Air 1%2C1 and Intrepid)

Thanks! I had checked (and forgotten) this link long ago. Even though it is about the MacBookAir1,1 it is good to read again.

> The SSD is not really tested in any setup. Also, I have currently no working external monitor setup.

The external monitor is not very critical to me right now, so the SSD is my main concern.

---

### Post by xavier10 on 2008-10-23
> **cyberdork33 said:**
> The SSD should look to the OS like any other internal storage device (hard drive).

I would guess so and also expect any fs to work on it, but then there may be some wear leveling issue. I know there are some filesystems targeted at SSD (YAFFS, just to name one), but am not sure whether this is mainstream in Ubuntu or not.

> Can you please verify the version number is MacBookAir2,1 ? It appears in System Profiler.

Right now, the machine has not been shipped yet (actually, I think they will ship in early november). I am just preparing the installation right now (and if someone says there is a fatal issue with this new laptop, it is still time for me to look for other solutions.

Of course, when I get it, I will report about my findings here, if I go the Ubuntu way, which I plan to do.

---

### Post by heluani on 2008-11-28
How did your installation go? I just got that model and I'm having big issues trying to get ubuntu there. 

The issue: 

- partition with bootcamp

- put the 8.10 server amd64 cd in the drive and reboot

- boot from the cdrom (not the apple superdrive, but a liteon)

- just after hitting enter in "Install.." the screen goes black, the driver stops spinning and the computer hangs

- After a reboot, the USB port is dead!

I don't know if it is the DVD drive (which works just fine with other computers), Installing Linux (I can't explain this phenomena this way, but someone here might be able to blame the installer for this) or just a bug in the macbook Air. Either way, certainly the Air has some issues cause its USB port shouldn't die out of nothing. 

To be clear again, after what's described above, the USB port doesn't transmit data to any device, not only the drive, but a mouse, an iPod, etc. The power line seems to be fine, as an optical mouse would light, but no pointer movement.

Apple did change the computer but I'm reluctant to try again... I wanted to hear success stories before with a setup like mine:

Macbook Air 2.1 --- SSD --- 1.86 Ghz
Ubuntu 8.10 server amd64.

Thanks

R.

---

### Post by heluani on 2008-11-28
Hi there, well, there must be something really bad about this. I managed to install the desktop amd64 version with the apple superdrive this time. And after a reboot, the usb port is dead again!!!! no recognition of my phone, ipod nor superdrive!!!!. I still have the Linux partition now at least.

Is there anything I can do about this port? I can't bring this computer to the store again!

R.

---

### Post by heluani on 2008-11-28
Now I'm going crazy, the computer won't boot even with MAc os now, it gets to the rEFIt without a problem but then it won't boot either system... and since it doesn't recognize the USB port, I can't boot from CD!!!!!

R.

---

### Post by heluani on 2008-11-29
Well, I managed to wipe out the hard drive and install again Mac OS X over wireless. I still have a fried USB port and don't know how to fix it. Won't try again with Ubuntu on this machine for quite a while, at least until people try more with the Air 2,1

Just for people searching with Google

1) I did three different installs, with Apple's superdrive and with a different one. A server version and a Desktop version. All 64 bit versions. All ended up with a fried USB port and I was lucky twice that the Apple store decided to give me a new machine.

2) The third time I went there, of course they didn't give me a new machine just to try, but a nice "genius" noticed that changing EFI can fry the USB port and that reinstalling Mac OS might fix it (it didn't, but at least I now have a functioning laptop).

Hopefully someone else is going to experiment more with this issue. I'm not planning on installing Ubuntu on this one any time soon.

R.

Edit: if you cross this post and know how to revive the USB port, I'll appreciate if you reply here :)

Edit2: After several resets, a SMC reset did it for the USB port... not reinstalling Ubuntu in this Air anytime soon!.

---

### Post by xavier10 on 2008-11-29
Hi,

First of all, I am very sad to hear about your terrible experience. This sounds scary, and I cannot see how Apple could let EFI "possibly fry the only USB port this machine has"...

Regarding to my own install... so far it did not go anywhere, since I have not received the laptop yet. Indeed, it was ordered by my employer in the end, and the administrative process for this purchase has been ridiculously slow so far. I even wonder whether I will receive my laptop before the end of the year.

However, when I eventually get it, I may go another route, and install linux under VMWare Fusion. I have tried this on my older MBP, and it worked very well. Only thing is I will have less RAM to work with, since it will have to be shared between two running OSes.

---

### Post by heluani on 2008-11-29
Well, I am a sick person, after finding out that reseting the SMC will restore the USB port to life I decided to go ahead and give several tries to the install (the only explanation I can think of is that the Linux install was failing at some point and leaving the CD drive unproperly mounted, but then again, I know nothing about these things). After 24 hours straight I finally have a booting install of Linux. Hopefully you won't experience these problems!

R.

---

### Post by kosumi68 on 2008-11-29
> **heluani said:**
> Well, I am a sick person, after finding out that reseting the SMC will restore the USB port to life I decided to go ahead and give several tries to the install (the only explanation I can think of is that the Linux install was failing at some point and leaving the CD drive unproperly mounted, but then again, I know nothing about these things). After 24 hours straight I finally have a booting install of Linux. Hopefully you won't experience these problems!

R.

I am glad to hear that! Since you seem to be the first person running ubuntu on a MBA2,1 there are a lot of things to test - if you're up for it. For starters, there is [http://ubuntuforums.org/showthread.php?t=924096](http://ubuntuforums.org/showthread.php?t=924096), which helps provide basic applesmc support. It will also be interesting to hear your experience regarding the trackpad. You probably already know about the mactel PPA [https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA), which will help you get going with the trackpad.

Cheers!

---

### Post by heluani on 2008-11-29
Well, I was hoping not to be among the first ones running Ubuntu on a 2,1 Air :) and I was about to make a detailed post about my lack of success basically following most of the thing that's out there for Air 1,1... Anyhow, this post will summarise my status as of today... tomorrow might be a different thing :)

I'm running 
```
heluani@vino:~$ uname -a
Linux vino 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux
```
On a ```
heluani@vino:~$ sudo dmidecode -s system-product-name
MacBookAir2,1
``` I followed most -- if not all -- of the advice in [https://help.ubuntu.com/community/MacBookAir1-1/Intrepid]("https://help.ubuntu.com/community/MacBookAir1-1/Intrepid") and the relevant parts in [https://help.ubuntu.com/community/MacBook]("https://help.ubuntu.com/community/MacBook")

The things that surprisingly work with the mactel APP help are the keyboard backlight and the sensors read fine with the [hal-applesmc]("https://help.ubuntu.com/community/hal-applesmc") package. Wireless works out of the box just unloading ssb and loading the restricted modules. The superdrive works fine if it's there at boot time. iSight shows up in Ekiga fine. I can test for whatever you guys want.. I have some time, and I'm willing to run whatever you want as long as you explain it :)

The things that don't work and I'd like them to:

- Sound: The chipset is nVidia now: ```
lspci
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
```
and everything seems to be installed fine, but I still don't get any audio, with or without a headset. I'm running what I think should be the latest Alsa drivers:```
heluani@vino:~$ dpkg-query -l libasound2
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  libasound2     1.0.17a-0ubunt ALSA library

``` well, I'm clueless.

-Trackpad: out of the box I get two finger scrolling and two finger right clicking, but I can't get dragging and taping to work. Either editing xorg.conf, or adding a .fdi file as described [in the community page]("https://help.ubuntu.com/community/MacBook") doesn't change anything, and running the script mentioned there just spits ```
unable to find device appletouch
``` the modules appletouch and evdev are loaded.

Well that should've bored anyone here... if you guys can help with these issues I'll be as always grateful, if you need a tester for something, well, if you have patience, everything can be worked out.

- Suspend to ram, just tried it, it goes to sleep when closing the lid, but when opening, the leds in the keyboard light up, but the screen is black... this might be anything and I haven't tried anything yet... I'll post later.

- Screen brightness: the buttons F1-F2 just don't work.

- Video: I'm getting 1280x720 which is not the native resolution, will try to correct this later. Re-edit: corrected, it took several re-installations of the restricted drivers to work, don't know why.


R.

---

### Post by heluani on 2008-11-29
Was about to answer in your thread with the post of the smc test... but perhaps is better to keep it here. If you want I can post it in that thread too... here is the answer of scan-smc.sh [ATTACH]94651[/ATTACH] unfortunately I had already installed the module, if you want me to I can uninstall it and run the applesmc-test.sh of yours. Let me know if you want another test.

R.

---

### Post by kosumi68 on 2008-11-30
> **heluani said:**
> Was about to answer in your thread with the post of the smc test... but perhaps is better to keep it here. If you want I can post it in that thread too... here is the answer of scan-smc.sh [ATTACH]94651[/ATTACH] unfortunately I had already installed the module, if you want me to I can uninstall it and run the applesmc-test.sh of yours. Let me know if you want another test.

R.

Thanks for the SMC report! Please find attached a new version of applesmc-dkms for testing. Running the applesmc-test.sh and attaching the logs will suffice as a test. As always, if you want to appear with a Tested-by in the kernel logs, please send me a private message with name and email.

---

### Post by kosumi68 on 2008-11-30
> **heluani said:**
> 
-Trackpad: out of the box I get two finger scrolling and two finger right clicking, but I can't get dragging and taping to work. Either editing xorg.conf, or adding a .fdi file as described [in the community page]("https://help.ubuntu.com/community/MacBook") doesn't change anything, and running the script mentioned there just spits ```
unable to find device appletouch
``` the modules appletouch and evdev are loaded.


Your trackpad is using the bcm5974 module, so settings for appletouch will not work. The best way to get things working in your case is to

1. Make sure there are no synaptics section in your xorg.conf, as it will interfere with the new fdi settings

2. Copy the file /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi to /etc/hal/fdi/policy/ and edit it to your liking. Then restart hal and X (I have updated the instructions on the wiki).

Since this machine is unknown, it would be great if you could provide the output of
```

lsusb | grep 05ac

```
so we can check the version of the trackpad. Thanks!

---

### Post by heluani on 2008-11-30
lol, I was about to update this thread with the success in getting the trackpad to tap and found your answer here:)...

Anyway, I followed most indications in [the community page for the new aluminum mpb]("https://help.ubuntu.com/community/MacBook%20Aluminum") and realized I was messing in the wrong part of the fdi file. I finally got one finger taping at least by adding 
```
<merge key="input.x11_options.TapButton1" type="string">1</merge>
``` since my other laptop running linux is a Lenovo with a trackpoint, I need to use this trackpad a little longer to figure out if I need more tweaking, perhaps reducing the sensitivity to tapping could be good, I'll look that up.

Sound: Installed ALSA 1.0.18.a with the script alluded in the above mentioned link. Adding ```
options snd_hda_intel model=mbp3
``` to /etc/modprobe/options just gives headphones sound, but even running 1.0.18.a I don't have sound in the main speakers. The mic doesn't work either.

Here's the output you asked for
```
heluani@vino:~$ lsusb | grep 05ac
Bus 003 Device 002: ID 05ac:8505 Apple, Inc. 
Bus 002 Device 005: ID 05ac:820b Apple, Inc. 
Bus 002 Device 004: ID 05ac:820a Apple, Inc. 
Bus 002 Device 003: ID 05ac:8210 Apple, Inc. 
Bus 001 Device 005: ID 05ac:0223 Apple, Inc. 
Bus 001 Device 004: ID 05ac:8242 Apple, Inc. 

```

Thanks, 

R.

---

### Post by kosumi68 on 2008-11-30
> **heluani said:**
> lol, I was about to update this thread with the success in getting the trackpad to tap and found your answer here:)...


Good good!

> 
Here's the output you asked for
```
heluani@vino:~$ lsusb | grep 05ac
Bus 003 Device 002: ID 05ac:8505 Apple, Inc. 
Bus 002 Device 005: ID 05ac:820b Apple, Inc. 
Bus 002 Device 004: ID 05ac:820a Apple, Inc. 
Bus 002 Device 003: ID 05ac:8210 Apple, Inc. 
Bus 001 Device 005: ID 05ac:0223 Apple, Inc. 
Bus 001 Device 004: ID 05ac:8242 Apple, Inc. 

```


Ah - Apple did *not* change the trackpad on the MBA2,1, that is good news. The 05ac:0223 device is the same one I have.

Thanks!

---

### Post by heluani on 2008-11-30
> Ah - Apple did *not* change the trackpad on the MBA2,1, that is good news. The 05ac:0223 device is the same one I have. Glad to hear,  
there are two issues that really need solving:

1- The patch to gnome-power-manager from mactel ppa doesn't work at least with me. F1-F2 don't do anything and /sys/class/backlight/ is empty (this gets populated installing the module mbp_nvidia_bl from mactel, but that doesn't do anything either). Battery life sucks I guess mainly because of this. 

2-The sound/mic issue is a big problem for me.

---

### Post by heluani on 2008-11-30
> Thanks for the SMC report! Please find attached a new version of applesmc-dkms for testing. Running the applesmc-test.sh and attaching the logs will suffice as a test. As always, if you want to appear with a Tested-by in the kernel logs, please send me a private message with name and email. Ooops, missed completely this message. Attached you'll find the report....

R.

[ATTACH]94749[/ATTACH]

---

### Post by kosumi68 on 2008-11-30
> **heluani said:**
> Ooops, missed completely this message. Attached you'll find the report....

R.

[ATTACH]94749[/ATTACH]

Thanks, I was about to ask you about this :-) However, now that you have the new package, what is needed is to run the test script, to confirm that the new version is working as expected.

PS. That would the the script found here: [http://ubuntuforums.org/showpost.php?p=5817699&postcount=1](http://ubuntuforums.org/showpost.php?p=5817699&postcount=1)

---

### Post by heluani on 2008-11-30
> **kosumi68 said:**
> Thanks, I was about to ask you about this :-) However, now that you have the new package, what is needed is to run the test script, to confirm that the new version is working as expected...

Ooops, sorry about that, here's the test. Oddly enough, I did get a Kernel Panic when trying to suspend just after installing this new package... attached is also the dmesg booting just after that, just in case.

R.
[ATTACH]94779[/ATTACH]

[ATTACH]94781[/ATTACH]

---

### Post by kosumi68 on 2008-12-01
> **heluani said:**
> Ooops, sorry about that, here's the test. Oddly enough, I did get a Kernel Panic when trying to suspend just after installing this new package... attached is also the dmesg booting just after that, just in case.


Thanks for the logs - everything does seem normal. There has been some problems with suspend on the new macbooks, perhaps that is what you are experiencing.

I will wait a few days for other indications, before sending the patch upstream, just to make sure. I am uploading the new version of applesmc-dkms to the PPA now.

Thanks!

---

### Post by heluani on 2008-12-01
Actually, the suspend problem is intermittent so I guess it has nothing to do with applesmc-dkms. The only thing that pisses me off is the sound issue now (brightness seems to work on TTY, that's enough for me).

Thanks for everything... I'm quite happy having this functional, I think I'll wipe out mac OS X from this machine and reinstall Linux in the whole drive then.

R.

---

### Post by kosumi68 on 2008-12-04
upstream smc patch: [http://lkml.org/lkml/2008/12/4/43](http://lkml.org/lkml/2008/12/4/43)

---

### Post by heluani on 2008-12-04
Just checking, but this is included in the last applesmc you posted here right?

R.

---

### Post by kosumi68 on 2008-12-04
> **heluani said:**
> Just checking, but this is included in the last applesmc you posted here right?


Yes, and also in the mactel PPA version.

---

### Post by Sigudian on 2008-12-04
I'm getting a Macbook Air next month, i am going to set it up dualboot with ubuntu and I have some questions..

1. What is SMC?
2. Can I install ubuntu via a flash drive(like on PC)? (super drive is expensive and lousy)
3. I'm going to have two small partitions with the operating systems on, and one big share partition, how small can the OS partitions be?

Thanks, and also, to you who have one (dont want to hear this last question from anyone els, sorry), how is the Air? :D
Cant wait to buy one(cant afford one before the next payment after christmas) : /

Edit:
After reading up on minimum system requirements, I believe it is appropriate with 9gigs for OSX and 5gigs for Ubuntu.
Anyone know if i can go any lower, since I'm having home directory on separate partition. And does 5gigs for ubuntu count swapdisc?
And can you use a swap partition (same as ubuntu's) on OSX?

---

### Post by cyberdork33 on 2008-12-05
> **Sigudian said:**
> 1. What is SMC?

> **http://support.apple.com/kb/HT1411]The System Management Controller is an integrated circuit (computer chip) that is on the logic board of the computer. As the name implies, it is responsible for power management of the computer. It controls backlighting, hard disk spin down, sleep and wake, some charging aspects, trackpad control, and some input/output as it relates to the computer sleeping.[/quote]

[QUOTE=Sigudian said:**
> After reading up on minimum system requirements, I believe it is appropriate with 9gigs for OSX and 5gigs for Ubuntu.
I'd do 8GB for Ubuntu, and 9GB for OSX is quite small.
> **Sigudian said:**
> Anyone know if i can go any lower, since I'm having home directory on separate partition. Whoa that is a bit different than just having a "big shared partition". Are you planning to use one home partition for both Operating Systems? That can be a bit tricky.
> **Sigudian said:**
> And does 5gigs for ubuntu count swapdisc?I'd say no. 
> **Sigudian said:**
> And can you use a swap partition (same as ubuntu's) on OSX?

I don't think so. OSX uses a swapfile. I think someone asked this before, but I don't remember the outcome. I am pretty sure it cannot be shared between the two though. remember that you really don't HAVE to have a swap partition for Ubuntu. You do need one if you plan to use hibernation though.

---

### Post by kosumi68 on 2008-12-05
> **Sigudian said:**
> 
Thanks, and also, to you who have one (dont want to hear this last question from anyone els, sorry), how is the Air? :D


The Air is the best laptop I ever had, by far. However, there are currently some problems with support for the new MBA2,1. The MBA1,1 is working almost flawlessly (only the front mic does not work).

Partition-wise, I use this table on the 80Gb disk:
```

/dev/sda1 200Mb GPT
/dev/sda2 22Gb Linux root partition (/)
/dev/sda3 32Gb Linux home partition (/home)
/dev/sda4 6Gb  Linux swap
/dev/sda5 14Gb HFS+ OSX partition

```
The sizes are approximate, and does not completely fill the disk. I had to reinstall MACOS to end up with this partitioning.

---

### Post by Sigudian on 2008-12-06
To Cyberdork33 and kosumi68:

I want to have one home partition for both the two operating systems, after what I have read this is possible. I was thinking first about having two different home folders on one shared partition and linking them togetter by symblinks, but I found [a guide that went about sharing one home folder on one shared partition.]("http://www.tuxation.com/creating-home-partition-mac-linux.html") I also found more info regarding this on these forums. 

So i was hoping (these are what i hoped for, but the os discs may be a bit small)

```

Partition 1 - OSX system files (9GB)
Partition 2 - Ubuntu system files (5GB)
Partition 3 - Shared home directory (105GB)
```
Note: these are approximately how large the partition sizes would be, and the 3'd partition would mearly fill up the rest of wats left. And also, as far as I understand you can choose a different folder as a default installed apps folder in OSX so they will not take up space on the OSX system partition.

Any responce would be greatly apreciated.

---

### Post by cyberdork33 on 2008-12-06
> **Sigudian said:**
> I want to have one home partition for both the two operating systems, after what I have read this is possible. I was thinking first about having two different home folders on one shared partition and linking them togetter by symblinks, but I found [a guide that went about sharing one home folder on one shared partition.]("http://www.tuxation.com/creating-home-partition-mac-linux.html") I also found more info regarding this on these forums. 

So i was hoping (these are what i hoped for, but the os discs may be a bit small)

```

Partition 1 - OSX system files (9GB)
Partition 2 - Ubuntu system files (5GB)
Partition 3 - Shared home directory (105GB)
```Note: these are approximately how large the partition sizes would be, and the 3'd partition would mearly fill up the rest of wats left. And also, as far as I understand you can choose a different folder as a default installed apps folder in OSX so they will not take up space on the OSX system partition.

Any responce would be greatly apreciated.
Well, it is possible, but I wouldn't recommend that path. First, it is bad enough getting a good shared filesystem between the two. HFS+ (non-journaled) will work, but turning journaling off is really a bad thing... especially for the partition that you plan to keep all your saved files to. 

Secondly, since many utilities are common between Linux and OSX (unix) they will attempt to use the same config files in your home directory. (like the hidden .bashrc, .profile, as well as others). 

Also, you forgot the EFI partition at the beginning of the disc.

---

### Post by Sigudian on 2008-12-07
> **cyberdork33 said:**
> Well, it is possible, but I wouldn't recommend that path. First, it is bad enough getting a good shared filesystem between the two. HFS+ (non-journaled) will work, but turning journaling off is really a bad thing... especially for the partition that you plan to keep all your saved files to. 

Secondly, since many utilities are common between Linux and OSX (unix) they will attempt to use the same config files in your home directory. (like the hidden .bashrc, .profile, as well as others). 

Also, you forgot the EFI partition at the beginning of the disc.

Would you recommend using two separate home directory's on the same partition and linking them together. Not fully, but just common folders like "Pictures", "Videos", "Documents", "Shared", and so on???
If not, what would you recommend?

---

### Post by heluani on 2008-12-07
@Sigudian, I don't have much to say about the partition issues, it's just a matter of taste, but in my case I'd like to get rid of Mac OS X and just have Linux running.

About Intrepid in the Air. I'm having issues with suspend and with sound. With suspend: I get sometimes kernel panics closing the lid, sometimes the computer wakes up just after a few minutes and upon waking the screen brightness goes to zero which considering the fact that I can only change the brightness on TTY (using the non-open-source nvidia drivers) is kind of annoying. At the very least, this issues make the computer running Linux unreliable for travel for example.

Second issue I have is sound, It can only work with headphones at the moment, this is not major to me.

Answering your question about the Air as a piece of hardware: I can't really say much. It is a great looking computer, which is not important, and it is quite small and light, which is why you would get such a machine. On the other hand, there are models like the Lenovo X301 and such, which would make great travel computers also. In any case, I think this is a topic for a different thread

---

### Post by Sigudian on 2008-12-08
[COLOR="Navy"]@Heluani:

You would get rid of OSX huh? Well I only run Ubuntu now on my huge 17" (7.5 punds) PC laptop and the only problem I have with it at al (talking about linux compatibility) is the mic, everything els runs as smoothe as a babies butt. Though im getting this for its powerfull graphic chard (yes yes i know its a low end 9 series, but compared to the gf7000M I have now its heaven) and 1.8ghz CPU, and DDR3 ram (dont care how much it is, ram is over-rated, speed of ram is not) SO THATS why I'm getting the MAC, so show me any other laptop that has a better graphic-card to weight ratio, or even another ultraprotable with DDR3 ram :)

soooo, why keep OSX?? its cause ive tested (Thoraly) alot of different OS'es, including but not limited to dos, Windows3, win95, win 98, 2000, xp, vista, debian (and deb based), fedora based ++++ so ive been bashing OSX for so long for beeing the faggiest os without even trying it... So its OSX thoral review from me then....

Im dualbooting with Ubuntu so i always have a failsafe solution, and also It is calming that everything just works always after a decent configuration of the hardware :)
[/COLOR]

thats alot of off-topic,
anyway, what was the conclution about installing Ubuntu on the new Mac air,
I think its easier on the pour machine if you do it through bootcamp, i'm not shure, im just thinking out loud since he ruined his SMC (the OP i mean), but that aint no problem resetting anyway

---

### Post by heluani on 2008-12-08
> **Sigudian said:**
> 
anyway, what was the conclution about installing Ubuntu on the new Mac air,
I think its easier on the pour machine if you do it through bootcamp, i'm not shure, im just thinking out loud since he ruined his SMC (the OP i mean), but that aint no problem resetting anyway

I guess I am the guy mentioned in the quote as the OP since the actual OP didn't get his machine yet, and my previous post is all I can say about installing ubuntu in it. with an external drive it goes fine but bear in mind that you may have to reset several times the SMC, for some reason the installer just hangs immediately after starting. I'd recommend trying to ummount the drive immediately after installation finishes.

If you get either the suspend or the mic working fine, please post back here.

R.

---

### Post by Torlek on 2009-03-20
I ran in the same Problem heluani had. My understanding is that I have to try and reset the SMC until the installation works. Is there no workaround by now?

---

### Post by heluani on 2009-03-20
Not that I know. Note that Apple released a new EFI for MAcbook air 2,1 about a week a go. I haven't had time to install it and I don't know if that solves things or not. Please let us know back here if you got it working with the new/old EFI (for example I don't even know if this EFI will be supported by rEfit) and if you get alsa/sleep working.

Good luck with your installation!

R.

---

### Post by cputoaster on 2009-03-20
I was able to install triple-boot my MacbookAir2,1 (refit with osx, 8.10 64bit, vista 64bit) fine from a usb bd-drive. It worked just fine.

But I am not able to boot from the HD anymore, even if booting a life-image from an ubuntu 8.10 dvd-rom works. While grub works fine, booting older (-7) and more recent (-11) kernels just breaks somewhere after "ACPI: bus type pci registered". Resetting SMC and PRAM does not help. Might be the most recent EFI updates. Or some other strange thing...

I guess the next thing to try would be to try to boot the kernel from a usb memory stick or similar.

Other ideas?

Cheers,
A.

---

### Post by cyberdork33 on 2009-03-20
> **cputoaster said:**
> I was able to install triple-boot my MacbookAir2,1 (refit with osx, 8.10 64bit, vista 64bit) fine from a usb bd-drive. It worked just fine.

But I am not able to boot from the HD anymore, even if booting a life-image from an ubuntu 8.10 dvd-rom works. While grub works fine, booting older (-7) and more recent (-11) kernels just breaks somewhere after "ACPI: bus type pci registered". Resetting SMC and PRAM does not help. Might be the most recent EFI updates. Or some other strange thing...

I guess the next thing to try would be to try to boot the kernel from a usb memory stick or similar.

Other ideas?

Cheers,
A.
try acpi=off in the kernel line.

PS, Does rEFIt work with the new firmware?

---

### Post by cputoaster on 2009-03-20
thx for the tip, I forgot to mention that I tried all kinds of acpi (also apic and video) kernel options (I dont think video really matters, as it breaks so early). I also copied around the kernel to be sure it is not some file system thingy.

Yes, rEFIt works fine, it boots OSX and Vista64 and the ubuntu DVD without any problems. Booting from HD also seems to begin correctly, so I assume it is not rEFIts fault that it breaks afterwards.

Is there anybody successfully booting from HD with MacbookAir2,1 128GB SSD version?

---

### Post by heluani on 2009-03-20
> **cputoaster said:**
> 
Is there anybody successfully booting from HD with MacbookAir2,1 128GB SSD version?

I am running a -11 64bit kernel in that system with the new EFI (just upgraded) without problems. 

Although the last kernel upgrade (I upgraded it yesterday) broke my wireless network.

R.

---

### Post by Torlek on 2009-03-23
Well the Install went pretty much okay but I got only one sucessful boot so far. I did the rc.local edit for the wireless setup ([https://help.ubuntu.com/community/MacBookAir1-1/Intrepid#Wireless%20Setup](https://help.ubuntu.com/community/MacBookAir1-1/Intrepid#Wireless%20Setup)). But now the booting aborts shortly after loading grub. Either I get a restart, which breaks the USB port (again), or I get a black screen and a freeze or I get a black screen a freeze and a unhealty sonding triple beep.

I am using the -10 Kernel.

---

### Post by heluani on 2009-03-23
That's odd. I still get those restarts and the scary chime from time to time but only in this situation:


1) Boot with rEFIt and choose Linux and boot normally

If I reboot and repeat step 1) then everything's fine, otherwise:

2) Reboot and in rEFIt choose OS X. Sometime's I get a reboot at this step. but most of the time it's alright

3) Reboot in OSX into Linux.

It is here that invariantly, every single time, shortly after grub I get a reboot and/or the scary chime. Rebooting or pressing the power button twice and booting again is fine.

So in short, if I stick to the same OS it's fine.

---

### Post by cputoaster on 2009-03-29
At least I am not alone ;-). For me it happens all the time, like Torlek. Even if I reset PRAM and SMC before booting into linux. 64bit -11 kernel. Any other ideas? I also tried booting Jaunty and 8.10 32bit from the usb cdrom I*originally installed 8.10 64bit from, but it crashes after selecting "Install" in the bootloader. Any other ideas?

---

### Post by cyberdork33 on 2009-03-29
> **cputoaster said:**
> At least I am not alone ;-). For me it happens all the time, like Torlek. Even if I reset PRAM and SMC before booting into linux. 64bit -11 kernel. Any other ideas? I also tried booting Jaunty and 8.10 32bit from the usb cdrom I*originally installed 8.10 64bit from, but it crashes after selecting "Install" in the bootloader. Any other ideas?
make sure you burn those disks slowly... they tend to come out as duds when burned fast.

---

### Post by cputoaster on 2009-03-30
Thx for the hint. I can try again, but I guess its pretty unprobable that the two kernels on HD that worked 2w ago plus the ca. 6 other kernels on ISOs burned with the apple iso burn tool (which verifies all burnt isos after writing) all halt / reboot at more or less the same line because of disk corruption. The disks also boot very well on a MacBook Pro. I also tried some other rescue disks (2.6.28 stock, 32bit and 64bit). How I miss the serial kernel debug console on a macbook air... I will have to compile the latest stable git kernel, create an isolinux cd and see if this fares any better. Or any more hints?

---

### Post by cyberdork33 on 2009-03-30
> **cputoaster said:**
> Thx for the hint. I can try again, but I guess its pretty unprobable that the two kernels on HD that worked 2w ago plus the ca. 6 other kernels on ISOs burned with the apple iso burn tool (which verifies all burnt isos after writing) all halt / reboot at more or less the same line because of disk corruption. The disks also boot very well on a MacBook Pro. I also tried some other rescue disks (2.6.28 stock, 32bit and 64bit). How I miss the serial kernel debug console on a macbook air... I will have to compile the latest stable git kernel, create an isolinux cd and see if this fares any better. Or any more hints?
Apple's optical drives are very picky... I had to go through 5 or 6 disks on my old iBook before a Linux CD was good enough to install from. Newer machines are better, but they can have their issues too.

 read back through the post history, and you are right... it just sounds like a kernel bug. IDK what else to tell you... other than it is likely ACPI related since it stops there. (and the newer MacBook5,2 is also having ACPI issues...).

---

### Post by cputoaster on 2009-03-31
Ok, so I tried a plain stock kernel booting from a self-made isolinux dvd containing just isolinux and a stock 2.6.29-git6 kernel, same problem. I am slowly running out of ideas. Will try with different configurations.

---

### Post by cyberdork33 on 2009-03-31
> **cputoaster said:**
> Ok, so I tried a plain stock kernel booting from a self-made isolinux dvd containing just isolinux and a stock 2.6.29-git6 kernel, same problem. I am slowly running out of ideas. Will try with different configurations.
You can try booting via EFI:
[http://ubuntuforums.org/showthread.php?t=995704&page=53](http://ubuntuforums.org/showthread.php?t=995704&page=53)

---

### Post by cputoaster on 2009-04-09
Yes, that worked, thanks

---

### Post by rileyporter on 2009-06-26
To fix the USB port after it stops working during install or whenever:

hold down the left SHIFT-CONTROL-OPTION
Tap the power button.   
Let go of the keys.

Press the power button after 5 seconds.  

USB should work.

I too have a macbook air 2,1 and my issues are:

F1 - F2 Does not work for backlight.
Sound

 does not work in speakers.

A bit of an annoyance is how touchy the touch pad is with my wrist bumping it and screwing while typing.

Riley

---

### Post by kristina-dev on 2009-10-16
Hi!  I just got a MacBook Air 2,1 and I'm trying to install 32-bit desktop Ubuntu 9.04 on it.  When I remove [FONT="Courier New"]splash[/FONT] and [FONT="Courier New"]quiet[/FONT] and add [FONT="Courier New"]noapic[/FONT] and [FONT="Courier New"]acpi=off[/FONT] (from [https://help.ubuntu.com/community/MacBookAir2-1/Jaunty/](https://help.ubuntu.com/community/MacBookAir2-1/Jaunty/)), it hangs on:

[FONT="Courier New"][    0.350294] EISA bus registered[/FONT]

I also found install instructions at [http://bloggis.se/atte/94921](http://bloggis.se/atte/94921), so I tried just adding [FONT="Courier New"]noapic[/FONT], which seemed to get it slightly further, but it still hung at:

[FONT="Courier New"][    0.896740] ACPI: bus type pci registered[/FONT]

Does anyone have any idea what might be going wrong?

---

### Post by heluani on 2009-10-16
just try a couple of times, are you ticking on the menu or adding it directly to the kernel command line args. I'm now in the process of building a CLFS on a Macbook Air 2,1 (want to test why the hell Alsa doesn't read the mic) and can boot a Karmic Live CD without trouble.

R.

---

### Post by kristina-dev on 2009-10-18
I tried multiple times with the same result. I got a little further by using the kernel parameter pci=bios. It finishes the kernel stuff now, but then hangs a while and displays a BusyBox initramfs prompt that is either a) frozen or b) my keyboard doesn't work. 

Any ideas?

---

### Post by heluani on 2009-10-18
beats the hell out of me, but just to check though, I'd try with either an intrepid live cd and/or a Karmic one, both of those worked without a hitch for me (haven't tried a Jaunty one).

R.

---

### Post by kristina-dev on 2009-10-18
Thanks for the advice, sorry to keep spamming the thread, but I'm hoping something rings a bell with someone...

I tried Karmic, as you suggested (and Intrepid, but that didn't go as well), and got slightly farther.

I'm using noapic, pci=bios, and all_generic_ide as boot params, and it finishes the kernel stuff and starts trying to load the fs.  It gets to /scripts/casper-premount, prints "Done" twice, then dumps me into the busybox prompt.  A second or two later it prints "unable to find a medium containg a live file system" to the prompt.  

My keyboard is still dead at the busybox prompt, I'm thinking it might have something to do with the modules for it not being loaded.  I think maybe it unloads the CD driver, too, that would explain why it can't find the file system.  Maybe.  

Anyone know a modprobe-type boot arg?

---

### Post by atte on 2009-11-11
I had similar problems like you guys, I scribbled down my fix here:

[http://bloggis.se/atte/99928](http://bloggis.se/atte/99928)

...or the short version: acpi=noirq pnpacpi=off

---

### Post by heluani on 2009-11-12
> **atte said:**
> I had similar problems like you guys, I scribbled down my fix here:

[http://bloggis.se/atte/99928](http://bloggis.se/atte/99928)

...or the short version: acpi=noirq pnpacpi=off

With these parameters I boot just the same as always and this doesn't solve the usual issues I had before (no suspend to RAM nor poweroff on rc level 1). It is true that I got rid of Ubuntu and I'm only running an LFS on this macbook air 2,1 so it's not clear what the issues are though. Most annoying are the tsc clocksource unstable messages, I think they are related to the scheduler.

R.

---

### Post by andrkavr on 2009-12-29
I find the only way to make this rotten apple 2,1 boot after a SMC reset (shift-ctrl+alt+power button), which is needed every time it's not properly shut down, is to boot into OSX first.
It's annoying, but I can live with that; but the thing I can't quite understand is how the audio problem is still here after more than a year. Or did someone get the speakers working and forgot to tell everyone? ;)

I thought I was lucky, when I got my old Air (1,1) replaced because of a slight hinge defect... *sigh*

---

### Post by heluani on 2009-12-29
> **andrkavr said:**
> but the thing I can't quite understand is how the audio problem is still here after more than a year. Or did someone get the speakers working and forgot to tell everyone? ;)

This must be an EFI issue or something like that. I got rid of ubuntu and installed a Linux from scratch just to diagnose that very same issue, but no luck yet. Let's hope that someone in the ALSA team buys one :)

Anyway. the ACPI issue is much worse, I'm hoping this will get fix with a kernel upgrade soon.

R.

---

### Post by andrkavr on 2010-01-12
> **heluani said:**
> 
Anyway. the ACPI issue is much worse, I'm hoping this will get fix with a kernel upgrade soon.

R.

It seems that with the latest kernel (2.6.32-5) and acpi updates in debian unstable, this issue is dealt away with. The system now boots even after an unclean shutdown, with or without smc reset and without the need to boot OSX first. 

There are some issues with suspend to ram, which renders the system useless (screen goes blank, Xorg hogs the cpu), but that's not necessarily related. ;)

---

### Post by heluani on 2010-01-21
> **andrkavr said:**
> It seems that with the latest kernel (2.6.32-5) and acpi updates in debian unstable, this issue is dealt away with. The system now boots even after an unclean shutdown, with or without smc reset and without the need to boot OSX first. 


Just compiled vanilla 2.6.33-rc4 from GIT master and I don't see any changes in the ACPI errors. It could be Debian patches as you mention, but I've been looking at the commit logs and I can't find anything that could be relevant to macbook air.

R.

---

### Post by heluani on 2010-02-21
Well, playing with Hda-Analyzer [http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer) I got my main speakers working. 

To have audio on the main speaker just make sure that the pin at node 0x18 has  its amp_out unmuted, and under widget control check the pin_out and vref anything that is not HIZ. Under connection list check any of the mixers 0x0c, 0x0d or 0x0e and go to that node. In that mixer unmute under Input Amplifier the first two values and max out the values under "Output Amplifiers" 

Try your results with aplay. 

To get audio on the headphones you do something similar with the pin in node 0x14, although I couldn't find how to switch the main speaker off when the hp jack is in use (at least not from hda-analyzer). I haven't figured out how to get the mic working, perhaps someone here with a little more free time? :)

Anyway, this should mean that we're closer to proper ALSA support on this machine.


Cheers,

R.

---

### Post by heluani on 2010-02-22
Here's a patch to patch_realtek.c in the kernel tree to add support for internal speaker and headphones. I couldn't find the mic yet. If you don't know how to apply this then wait a bit, at some point something like this will make it downstream. This adds a model mba21 for the snd-hda-intel driver. It would be great to have testers.

enjoy.

R.
[ATTACH]147956[/ATTACH]

---

### Post by andrkavr on 2010-03-05
Great work!

Finally it works.
Couldn't test it earlier, because of broken kernel headers in debian squeeze (from 2.6.30 on), but works great now.

if anyone else has trouble compiling alsa on debian squeeze 686, the solution, until the packages are fixed, is to link:
/usr/src/linux-headers-2.6.3x-x-686/Module.symvers --> /usr/src/linux-headers-2.6.3x-x-common/Module.symvers
/usr/src/linux-headers-2.6.3x-x-686/include/config --> /usr/src/linux-headers-2.6.3x-x-common/include/config
/usr/src/linux-headers-2.6.3x-x-686/include/linux/utsrelease.h --> /usr/src/linux-headers-2.6.3x-x-common/include/linux/utsrelease.h
/usr/src/linux-headers-2.6.3x-x-686/include/linux/version.h --> /usr/src/linux-headers-2.6.3x-x-common/include/linux/version.h
/usr/src/linux-headers-2.6.3x-x-686/include/linux/autoconf.h --> /usr/src/linux-headers-2.6.3x-x-common/include/linux/autoconf.h
/usr/src/linux-headers-2.6.3x-x-686/include/linux/bounds.h --> /usr/src/linux-headers-2.6.3x-x-common/include/linux/bounds.h
/usr/src/linux-headers-2.6.3x-x-686/include/linux/compile.h --> /usr/src/linux-headers-2.6.3x-x-common/include/linux/compile.h

And then get the alsa snapsjot and compile. ;)

---

### Post by heluani on 2010-03-05
> **andrkavr said:**
> Great work!

Finally it works.
Couldn't test it earlier, because of broken kernel headers in debian squeeze (from 2.6.30 on), but works great now.


Glad I helped, the patch made it through the ALSA/kernel repositories, it should be in for 2.6.34 I still can't get rid of OSX because of the mic issue ( I want to use this computer as a travel one ) I suspect that we need vendor specific coefficients in nid 0x20, but without the datasheet for ALC889a that could be impossible. Also, I do not know how ALSA works, but from the vendor id, the card reads more like a ALC885 than a 889a, so I don't know why it's recognized as a 889a. In any case, I couldn't find anything in the ALC885 datasheets that would help us in the mic issue. In all the 885 models, pin 0x18 is the mic and 0x14 is front. In our box we have 0x14 to be HP and 0x18 to be main speaker.... What we need is people with hda-verb spending their nights until we get this solved!.

R.

---

### Post by heluani on 2010-08-07
Just to bump this thread and add little info in case someone here knows something more. I've contacted the Hackintosh community ([ in this thread]("http://www.insanelymac.com/forum/index.php?showtopic=220090") ) in the hopes that they would know something more about alc885. I'm hoping that one might find some info on OSX to patch properly the alsa driver. But I can't find anything specific to this codec following the guidelines that the people in the mentioned thread gave me. 

R.

---

