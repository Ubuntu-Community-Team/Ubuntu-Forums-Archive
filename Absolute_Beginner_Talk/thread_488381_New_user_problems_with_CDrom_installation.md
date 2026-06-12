---
title: "New user problems with CDrom installation"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by Herbernator on 2007-06-30
Hi all,

I'm a new xubuntu user (well, I've never used it before... I'm trying though)
I'm trying to install Xubuntu alternate install "xubuntu-7.04-alternate-i386" via CDrom.

I boot from the CD ok, menu comes up and I select Install (the first option)
I get through location, keyboard and I start getting into troubles when it searches for a cd drive.

It cannot find a CDrom driver.

I have done that checksum utility and the CD is ok.

--Could someone tell me where to get Xubuntu drivers for LG cd Drive's from?

I have disconnected one CD drive (just in case there was a conflict or Xubuntu did not understand 2 CD drives... I dunno... I'm in the dark) Same problems

Both CD drives worked perfectly (in fact the whole computer worked perfectly) under Windows 2000.

Another quick question, the install program seems to be exceptionally slooooow! It takes about 10 minutes to get to the "looking for cdrom"
Is this normal?

Some information about the computer in question.
Intel P3 866mhz
128MB ram
LG CD/RW model no: GCE-9523B
LG cD/r model no: CRD-9522B
20GB Hard disc.

Thankyou in advance.

Herbernator.

---

### Post by sad_iq on 2007-06-30
What happends when you try the live cd? Also burn your iso at a low speed(4x-8x) and check the cd for defects as well(when you boot).
 If it still fails read this: [http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093) 
and this: [http://ubuntuforums.org/showthread.php?t=427540](http://ubuntuforums.org/showthread.php?t=427540)

---

### Post by Herbernator on 2007-06-30
> **sad_iq said:**
> What happends when you try the live cd? Also burn your iso at a low speed(4x-8x) and check the cd for defects as well(when you boot).
 If it still fails read this: [http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093) 
and this: [http://ubuntuforums.org/showthread.php?t=427540](http://ubuntuforums.org/showthread.php?t=427540)

I first downloaded the Live CD but it did not work... sent a message in this forum and the people said that there wasn't enough memory on the computer.... I believe the live CD requires 192mb ram whereas I have 132mb

I have burnt the CD at 4.0 speed.... the check for cd for defects option doesn't work properly.

I'll check out the links you have suggested.
[edit] Have checked out the links.... they are for computers that don't have CD drives or to install from USB drives..... Both my CD Drives work... (I can boot up ok)

Thanks,  very much appreciated.

Herbernator.

---

### Post by ayenack on 2007-06-30
Are both your CD drives on one IDE Channel or is one on Primary and the other on Secondary? The reason I ask is that you may not have the drive you are trying to use set to Master. This may cause some problems. If your comfortable with innards of your PC you can check this by looking at the jumpers on the back of the drives and checking them with the top of the drive where it'll tell you how to set the jumpers accordingly. If you have two hard drives it's almost certain that you have one on IDE1 & the other on IDE2 which in most cases would mean that the CD Rom's would be set to Slave.

---

### Post by Herbernator on 2007-06-30
> **ayenack said:**
> Are both your CD drives on one IDE Channel or is one on Primary and the other on Secondary? The reason I ask is that you may not have the drive you are trying to use set to Master. This may cause some problems. If your comfortable with innards of your PC you can check this by looking at the jumpers on the back of the drives and checking them with the top of the drive where it'll tell you how to set the jumpers accordingly. If you have two hard drives it's almost certain that you have one on IDE1 & the other on IDE2 which in most cases would mean that the CD Rom's would be set to Slave.

I'll check that.... but before I check if there was a problem wouldn't windows 2000 pick that up?
Both CD Drives worked perfectly under Windows 2000.

At this point, I'm willing to try anything.... I'm even tempted to chuck the pooter out the window if that would help ;)

Herbernator.

---

### Post by sad_iq on 2007-06-30
> **Herbernator said:**
> 
I have burnt the CD at 4.0 speed.... the check for cd for defects option doesn't work properly.
Herbernator.
 Then maybe your cd is faulty...but what happened when you tried checking it??
 Also try what **ayenack** said as he is right about that!!!
 If possible try booting another live cd like Puppy Linux that will work just fine with your spec...and see if it will boot. It takes less than 150 MB...so it should be easy to download!!!
 Go here: [ftp://ibiblio.org/pub/linux/distributions/puppylinux/](ftp://ibiblio.org/pub/linux/distributions/puppylinux/) 
   and download the puppy-215CE-Final.iso

---

### Post by Herbernator on 2007-06-30
> **sad_iq said:**
> Then maybe your cd is faulty...but what happened when you tried checking it??
 Also try what **ayenack** said as he is right about that!!!
 If possible try booting another live cd like Puppy Linux that will work just fine with your spec...and see if it will boot. It takes less than 150 MB...so it should be easy to download!!!
 Go here: [ftp://ibiblio.org/pub/linux/distributions/puppylinux/](ftp://ibiblio.org/pub/linux/distributions/puppylinux/) 
   and download the puppy-215CE-Final.iso

OK checked some things.

I have physically DISCONNECTED one cd drive (so I only have one CD Drive), rebooted and the installation still doesn't work. Swapped connections to the other CD Drive and that doesn't work either.

Both CD drives work ok..... they are completely operational.... is there any reason that a fully functioning CD drive would work with windows and not with Xubuntu? I have searched with google looking for this driver disc the install program asks for but no luck as yet.

If I can BOOT an Xubuntu install CD with a CD Drive why does the installation fail with the SAME CD DRIVE? It defies reality! It's not like I am taking the cdrom out while installing or anything like that.

I'm not saying that this install program is broken.... NO! ..... I know I doing something wrong. This is got me completely stumped.

Again thankyou all for your assistance.

Herbernator.

---

### Post by alienexplorers on 2007-06-30
I have the same CD's as you and I am running on a relativly slow machine.  I had no problems loading Ubuntu and it runs fine.

---

### Post by Herbernator on 2007-06-30
> **alienexplorers said:**
> I have the same CD's as you and I am running on a relativly slow machine.  I had no problems loading Ubuntu and it runs fine.

Thanks for that..... as I have said in previous posts.... I must be doing something wrong but I don't know what it is?

At the end of the CD drive detection.... it says that it couldn't find a CD drive. After that it says that I can install a driver from the Xubuntu installation cdrom or from a floppy disc. Could you tell me what you did?
If it was from a floppy, could you tell me where you got the driver from?

If someone could say to me hey... you selected this when I have selected that I'd be real happy.

My hard disc is formatted windows98 is that a problem?
Would it be better to reformat the hard disc?
I don't want anything fancy like a dual boot. I just want Xubuntu.

Herbernator.

---

### Post by alienexplorers on 2007-06-30
I did not have to do anything.  Just inserted the live CD and told it to install.  Answered some questions and 30 minutes later ubuntu was up and running.  That is why I can not figure out why yours will not load correctly.  It has me baffled and I am still trying to figure out what to tell you.  The only thing I see that might be a problem is the amount of ram.  I think all versions of ubuntu, xubuntu, & kubuntu require more.  This still does not explain the cd problem.

---

### Post by RedSquirrel on 2007-06-30
Xubuntu is supposed to be able to install from the alternate CD with as little as 64 MB of RAM, so I don't think that's the issue.

I am concerned about the fact that the "check CD for defects" option doesn't work properly. Can you be more specific? What happens when you try to check the CD?

---

### Post by Herbernator on 2007-07-01
> **RedSquirrel said:**
> Xubuntu is supposed to be able to install from the alternate CD with as little as 64 MB of RAM, so I don't think that's the issue.

I am concerned about the fact that the "check CD for defects" option doesn't work properly. Can you be more specific? What happens when you try to check the CD?

Hi again... thanks all for your help.

When I try to check the cd on the "alternate" installation cdrom (just to clarify things) from the main menu nothing seems to happen. (to be honest.... I pressed the "check CDrom" option and went and did something else for 10mins then came back to a BLACK screen. Neither the cd drive light nor the HDD light was on (to tell me that something was at least happening) I then waited another 20 minutes and rebooted the computer.

I re-burned another cd (at 4times speed) just in case there was a problem with the cdrom.

I have installed Operating Systems before (Not linux tho, Dos,Windows3.1,95,98,2000,nt,xp, PICK,Novell,etc.etc.).... so I'm not new to learning on the job. This has got me completely stumped.

Is there any pre-preperation required for the hard disc.... eg formatting for linux?, a formatted HDD?
All I would like is a nice xp style interface that will run openoffice and a solataire game (nothing else)

Again thanks for your help

Herbernator.

---

### Post by mastersync on 2007-07-01
I think we have the same problem. The screen went blue forever.

I think this problem have something got to do with CD-Drive. I assume you have the external cd-drive, not usb.

I'm still stuck tough.

---

### Post by bigbrownbear on 2007-07-01
I'm not a techie so I can't offer technical ideas.  I had problems with launching some Ubuntu applications recently, and found that the source was a faulty copy disc.  I did a new install with a Canonical disc and no problems, so the bug may be in the origin of your disc.  Can you get your hands on a Canonical disc for installation?  Also, try hooking up an external drive and installing through that.

---

### Post by Herbernator on 2007-07-01
[QUOTE=mastersync;2944108]I think we have the same problem. The screen went blue forever.

I assume you have the external cd-drive, not usb.QUOTE]

No.. both of my cd drives are INTERNAL

I do remember the blue screen lasting quite a long time, but after that, the install prog does something.

Herbernator.

---

### Post by Herbernator on 2007-07-01
> **bigbrownbear said:**
> I'm not a techie so I can't offer technical ideas.  I had problems with launching some Ubuntu applications recently, and found that the source was a faulty copy disc.  I did a new install with a Canonical disc and no problems, so the bug may be in the origin of your disc.  Can you get your hands on a Canonical disc for installation?  Also, try hooking up an external drive and installing through that.

I got the Xubuntu alternate cd ISO from here: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/xubuntu-7.04-alternate-i386.iso](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/xubuntu-7.04-alternate-i386.iso)

This place is the RECOMMENDED place to download from the OFFICIAL xubuntu website. Could you be suggesting that this is not the correct download to get?

---

### Post by splintercellguy on 2007-07-01
I believe he's suggesting that you did a bad burn. Try doing it at 1x, and do the CD check.

---

### Post by Herbernator on 2007-07-01
> **splintercellguy said:**
> I believe he's suggesting that you did a bad burn. Try doing it at 1x, and do the CD check.

I have burnt this ISO three times so far. All at 4 times speed and at all times infrarecorder, also the recommended software to burn iso's, says the burn was successful.

I don't know what to do..... I'll give this installation one more try and see.

Herbernator.

---

### Post by Herbernator on 2007-07-01
Hi all, 

I've just re-tried for approximately the 20th time and now am giving up.

I'm sick and tired of pulling cd drives out and in, playing around with this and that. Xubuntu didn't do as I was told it would do. It just doesn't work!

I joined this forum in the hope that I would recieve help. (Hopefully from someone who helped write the software) While I have had a few suggestions to try this and that nothing has worked, and the slowness of the replies shows that no-one is really interested.

I totally understand that you get what you pay for..I paid nothing therefore I recieve nothing. I also now understand why new users are a little afraid of getting into into Linux.

**I must say thankyou to all people who replied to my message. I am very greatful.**

I haven't given up on Linux totally, I'll try another distro, but as to all my friends and contacts, I can only say that Xubuntu does not work (for me at least).

Thanks again.

Herbernator.

---

### Post by alienexplorers on 2007-07-01
Try putting a live-cd disc in each cd-drive and try loading that way,

---

### Post by RedSquirrel on 2007-07-03
@Herbernator:

Sorry to hear you're having so much trouble.

Did you check the md5 sum of the download?

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

I understand your frustration. Just for your information, the developers rarely (if ever) visit these forums. As far as I know, ubuntuforums is almost exclusively "users helping users". We're all volunteers here and your problem is unusual. Most people would gladly give you an answer if they had one to give.

Xubuntu does work for a lot of people. If you want to try another distribution, I wish you the best of luck. :)



> **alienexplorers said:**
> Try putting a live-cd disc in each cd-drive and try loading that way,

The machine in question only has 128 MB RAM. The live-cd install requires a minimum of 192 MB.

---

### Post by Herbernator on 2007-07-04
> **RedSquirrel said:**
> @Herbernator:

Sorry to hear you're having so much trouble.

Did you check the md5 sum of the download?

I understand your frustration. Just for your information, the developers rarely (if ever) visit these forums. 

Hi all, 

I want to say first of all that my previous post was a little bit nasty towards Xubuntu and these forums and  ..... I SINCERLY APOLOGISE.

I managed to get my hands on another computer and YES, XUBUNTU INSTALL PROGRAM WORKS IN EVERY WAY!!!!! I installed Xubuntu and it works.

It was the computer that is buggered! I have done some further testing on it (the Xubuntu installl disc Memory Test and all I get is error upon error) My memory or my system board must be stuffed!

Again, for the record, I blamed this forum and Xubuntu for not working. THIS IS NOT THE CASE!

I'm sorry.

Kind regards to all. Thankyou again to all that replied to this message.

Herbernator.

TOPIC CLOSED

---

