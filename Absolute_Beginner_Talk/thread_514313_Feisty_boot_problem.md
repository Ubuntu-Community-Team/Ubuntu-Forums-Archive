---
title: "Feisty boot problem"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by DiBiddilyBop on 2007-07-31
Hi there.  I´m a complete noob when it comes to Ubuntu and Linux in general, so please forgive my ignorance.  I have tried searching the forums for a solution and have yet to find exactly the same thing I am experiencing or a fix that works, so I´m posting hoping to find a solution.

I installed Ubuntu yesterday and have been having several boot problems.  At first I had problem loading Ubuntu (which I mention because I think it´s related to the problem).  When I tried booting from the CD, the menu came up and I could make selections, but choosing install or booting in safe graphics mode resulted in the same thing: the monitor going to sleep and no hard drive or CD ROM activity.  I then downloaded the alternate install CD and was able to install Ubuntu 7.04 just fine, but now when I boot up, the same thing happens.  It gives a message that the kernel is loaded, and then the monitor hibernates.  No HDD activity, no sounds, no progress bar.  I was able to hit escape and load into the command line interface, which I used to apply the fix for my Radeon X800 and start Ubuntu.  At that point I thought I was fine, however when I reboot, it still does the same thing with the monitor going to sleep right after the kernel is loaded.  The weird thing is I can go into the command line and just startx to get in without making any changes.  At no time am I prompted to log in (probably because of the work-around method of getting in?) which is causing some other problems.  So there´s the symptoms, here are my system specs:

Asus K8V motherboard
Athlon 64 2000+ processor
ATI Radeon X800 Pro video card
Planar 19"LCD monitor

Any help would be very appreciated.

---

### Post by aspen_dv on 2007-07-31
Do you have any other linux partition on your hard drive? Make sure to remove any USB drive, thumb drive, then try to boot from the CD again.

---

### Post by DiBiddilyBop on 2007-07-31
Thanks for your response, aspen_dv.

No, no other partitions on the drive.  I do have a second internal, NTFS hard drive that I have since disconnected to see if that is causing the problem and the same thing happened.  I guess it´s ¨recovery mode¨ that I´m entering when I boot up each time.  I think the problem must originate with the loading menu that would show when my PC boots up or would have shown during the install.  Is that rendered or handled in some different way that would cause my PC to choke on it?  I´m just throwing out ideas since really I have no clue but would love to get things working.

---

### Post by DiBiddilyBop on 2007-07-31
Ok, a couple more interesting details.

The version of Ubuntu I loaded was the 64-bit version which I thought was fine given my AMD 64 2000+ processor.  I tried loading on Ubuntu Ultimate 1.4 which installed perfectly (which I realized after the fact is 32-bit).  Now when I reboot I have the same problem with the screen going black, but it appears like it's booting into the original 64-bit install as that's what it goes to when I go into recovery mode and do the startx command.

I'm going to do a little more playing around, but any more suggestions would be appreciated.

---

### Post by buixuanduong1983 on 2007-07-31
Did you check your iso file downloaded for consistence? I used to have some same kind of problem when I downloaded Ubuntu iso file: it still can boot, choose option... but cannot run correctly. You can use md5sum to check your iso and compare it with this list:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by DiBiddilyBop on 2007-08-01
Yeah... I've actually tried installing from three different disks now, made from a couple different computers (64-bit, 64-bit alternate, 32-bit Ubuntu Ultimate).  Haven't had any luck with any of them.

The good news is Ubuntu Ultimate actually looked like it went through the whole install process without a hitch, then when it rebooted, it got to the Grub loading and spit back Error 15.  So now at least I have something to work with when I get back home.  Although I'd like to get the 64-bit working, I really just want to take ubuntu for a test-drive and I can do that just as well with the 32-bit version as I can with the 64.

---

### Post by buntunub on 2007-08-01
Sounds to me like with all those various installs you tried, some things got setup/autodetected incorrectly and config files got screwed up. I would just format and do a fresh install of the buntu version of your choice this time, and just do that one. Try that and let us know how that works out.

---

### Post by DiBiddilyBop on 2007-08-01
Sorry, I should have mentioned it that I did format between installs.

I've only actually installed twice.  The first 64-bit disk wouldn't even go to install (black screen after I chose the install option), so I tried the alternate disk.  That install went through just fine.  I installed Ubuntu Ultimate over the top of that, but realized it wasn't working correctly when I still had to boot into recovery mode and saw the same desktop as my original install.  So I reformatted and installed Ubuntu Ultimate on a fresh formatted drive and everything looked just fine until the first reboot when I got the Error 15.  It was getting late so I haven't worked on it any more since (I'm pretty sure booting into recovery mode will still work but we'll see).

---

