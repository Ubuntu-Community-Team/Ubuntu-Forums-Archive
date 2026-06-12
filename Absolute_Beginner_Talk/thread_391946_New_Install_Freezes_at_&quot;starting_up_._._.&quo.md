---
title: "New Install Freezes at &quot;starting up . . .&quot;"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by taco2 on 2007-03-23
Hi, 
I am  trying for a server installation. 've made a successful desktop installation that went without any issues at all.  The problem is this server install, The machine boots off the Server 6.10 version CD.  The process completes after I respond to normal question.  I then tells me it is done with the install and to remove the CD, and allow the computer to reboot   On rebooting, it begins to start up, then comes to a line saying starting up ... and nothing further seems to happen.


The version is 6.10, 
the machine has a AMD Duron 1.6 chip, 
256 MB memory, 
a via ethernet card,
 the mother board is an ECS (something 7),
Can't remember the video card, but the video is fine during the install off CD process.

 I've tried two different hard disks.  A WD, 80 GB and a Hitachi Deskstar 165 GB.   Both drives had previously been in other boxes.   I checked that the install disk is valid

I've tried reading help files, but each time I find either information that is too basic, and then information that I don't yet understand.

---

### Post by i.am.canadian on 2007-03-23
Hey there,

How long did you did you wait after you rebooted?  I had a similar problem where I thought my computer wasn't going to start, but I had to wait a few minutes before the bar started to move at all.  I'm sure there is a fix for this once you get your system started, I just haven't had the time to look into it.

I hope this is just the case, but if not its beyond my depth.  Best of luck.

Cheers.

---

### Post by taco2 on 2007-03-24
Hi,

Well I left it overnight, and it stays frozen at "starting up . . . "

What I then did was use the recovering a broken system option, and I;m now able to get to a "shell"

It asks me "Device to use as the root file .."

I choose

/dev/hda1

(also available were chooses /dev/hda2, and hda3)

then the next choice I made execute a shell in 

/dev/hda1

Then I get to what must be a shell,  it has a command prompt that looks like #, and I got to figure out what to do next

---

### Post by taco2 on 2007-03-24
Adding more information.

In trying to debug this problem, I think it is better to boot to the recovery enviroment, because then it shows where the freeze occurs.

I was able to get a different result by turning the APCI=off, either with a command line, or in bios.  That is the boot sequence seems to go further when the power management is turned to disable in bios

But, then it is giving me a message of kernal panic.

I'm responding with person panic.

---

### Post by taco2 on 2007-03-25
I never got this solved, but in case someone reads this later here is what I learned

On boot, Use the escape and edit the grub menu to take out "quiet."  All the direction are on screen, read carefully. That way you will learn what is happening durig the boot.

The problem seemed to be with the need to set APCI=off, but the box still kept freezing when I did that.  It got further through the boot sequence.

Changing APCI in BIOS did not solve the problem either.

It was a ECS motherboard from Frys

---

