---
title: "Powerbook g4 installation problem."
date: 2010-08-08
forum: Apple Hardware Users
---

### Post by Ericatang on 2010-08-08
Alright, so I've got a powerbook g4 here that I obtained off a friend for free. Spec-wise it's pretty sparse.. But, I figured I would install ubuntu on it and just use it for light browsing here and there. 

Currently it's running Mac osx 10.1.. Which is practically useless by today's standards, and there are no modern browsers that support that old of a version of Mac osx.

Now, getting on to my problem..  this powerbook g4 has no screen. Literally, it's been ripped off. I'm not entirely sure why, but it's ripped off at the hinges. However functionally, everything on it works when hooked up to an external monitor, including the cd drive.

So this is where I run into a problem, when I insert the ubuntu cd (ppc 9.04), and hold down the c key.. That doesn't work, and it goes straight to the normal boot up of mac os.

But when I attempt to go to the option screen, by holding down the option key, there's no output to the external monitor.

The same thing goes for when I make it boot to open firmware, nothing's shown on the external monitor. However, I blindly typed in the command for booting from cd in openfirmware, in hopes that it would cause the ubuntu install to start, and give output to the external monitor,  no luck as far as external monitor output goes.. 

However, the cd drive did whirr in response, so I figure the command must've worked..

So.. Is there any way for me to force output to the external monitor when booting from cd so that I can actually do this install? :-s *I'm thinking it might be possible to try and make the system think the non-existent lid is closed,so that it will switch to external but I havent tried.*

---

### Post by khelben1979 on 2010-08-08
I assume you have connected the external monitor by USB. If that's true, then that's the cause of the problem to why you get no visible screen at bootup.

It is as you have figured out, that the Linux installer haveto be able to recognize your monitor through the USB port. In my opinion, that should not be a problem with a modern Linux distribution, but it looks like it is. 8-(

Are you sure that you have managed to "blindly" start the Ubuntu installer by typing the correct command on the keyboard?

Have you tried the same thing with Ubuntu Lucid?

---

### Post by Ericatang on 2010-08-08
Actually, that's the interesting part I'm using a normal VGA monitor connection, not usb.

As far as being sure goes, no. I don't really have any way *of* being sure :P

I haven't tried 10.04 on it, yet. If I'm going to try anything else next it'll probably be xubuntu.. I don't see why it would make a difference though.

---

### Post by B_Free on 2010-08-08
Let it start up in OSX. Put your cd in the drive. Does it show up on the desktop? If so, go to system preferences. Select hard drive. If the cd is pictured there (your Ubuntu disc), select it and restart.

---

### Post by Ericatang on 2010-08-08
Alright, it was detected by it, but said "You have inserted a disc that cannot be read by Mac OSX, continue with it inserted, eject, or initialize?"

I tried initialize, and it showed Ubuntu PPC in the disk utility window, but wouldn't let me mount it. 

I checked startup disk, and it only showed Mac OSx 10.1.5, and Mac os 9.

---

### Post by B_Free on 2010-08-08
A few questions.
Did you burn the iso image or did you just copy it to your cd? Is the iso file for PPC? How much RAM do you have?
Is the cd drive able to read cdw discs? Look in the System Profiler (About this Mac, then get info). If there is no support you will never mount it.

---

### Post by Ericatang on 2010-08-08
..I know how to burn an iso image, thanks.. xD. Sorry, I guess it was a legitimate question, but I'm not inexperienced with tech. And yes, it's obviously for ppc. 256mb of ram, yes it's able to read cd's.

---

### Post by B_Free on 2010-08-09
The reason why I asked was the cd will not mount on the desktop nor start up with the C depressed. Ram is the minimum. I've been working with Macs for 20 years. Thought I could help. I have installed Ubuntu, Debian, etc. on all my Macs. Something is wrong with the CD.
In my G4 I have a older DVD Rom and the disk is not recognized. In my other G4 there is a combo drive. The disk is recognized in it. If you have any other software disks, try them in the drive. If you have any other CDW disks that have Mac stuff on it, try it to see if it mounts. If those disks won't mount, then it is your CD drive that is the culprit. If they do, then it is the Linux disk that has something going on with it.

---

