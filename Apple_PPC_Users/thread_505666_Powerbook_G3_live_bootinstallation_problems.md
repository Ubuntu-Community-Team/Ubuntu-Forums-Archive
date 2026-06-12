---
title: "Powerbook G3 live boot/installation problems"
date: 2007-07-20
forum: Apple PPC Users
---

### Post by radicalspud on 2007-07-20
greetings

i'm attempting to install Ubuntu on a Powerbook G3 bronze. so far i've had little luck, and i've come up with some questions that i'm hoping can be answered at least somewhat by people who have more experience with this than me. i have a great deal of experience with Windows (i'm a system administrator) and quite a lot with Mac OS 9/X, including some work with the command line in OS X, and also some working familiarity with Knoppix and PuppyOS live CDs.  i have Ubuntu installed on one of my PCs, as well, which is useful as a reference for how it should work. i'm comfortable working from the command line, if i need to, but a lot of the Linux-specific stuff is really new to me, so i'm having difficulty getting where i need to go due to lack of information.

the powerbook has 256MB of RAM and a 14GB hard drive, which i am dedicating solely to Linux for the time being (due to the extra complication of trying to get OS X and Linux to work from the same drive.)

the first time i booted from the (GUI) live CD, i made it to the desktop, but there were all kinds of errors and module failures. (nautilus, bonobo-activation server) from what i've been able to find, it would seem that those were caused by the system date being set incorrectly, probably to 1904 since that is the default date when the PMU gets reset. in spite of this, i soldier on, hoping i can get it to install anyway.

partway through partitioning the hard drive (guided) the computer hangs. i reset it and try again, but now the live-CD boot hangs somewhere between the first command prompt and the desktop. this happens every time afterward until i give up. i pull the HD and repartition it on another computer (can't remember what scheme i used; the comp was a windows box). putting it back into the Mac, i once again succeed in getting the live CD to boot to the desktop, with the same series of errors and module failures. again i try to install and again it hangs partway through the partitioning.

now i cannot get it to boot from the live CD at all. i've tried booting from Mac OS X install CD and partitioning the drive that way, i've tried the alternate text-install CD (which won't boot at all), i tried the 6.10 Ubuntu install CD...i tried setting the RTC from open firmware to see if that fixed the problem. i've tried "video=ofonly" and "live-powerpc" booting options.

so here i sit. i'm at a loss as to how to proceed, but i know it's theoretically possible to get this to work. i know it will boot to the desktop from the live CD, but not reliably (like, every time).

questions:

*is it possible to do a verbose boot from the live CD? (perhaps i can figure out what is causing the hangup.)

*how can i partition the HD correctly from either the Mac OS X install disc or another linux installation, so that it will have the correct Apple_Bootstrap partition it needs? (i figure if i can get it partitioned separately from the installation process, i might have a better chance of getting it to install correctly.) i need REALLY SPECIFIC information on this process. i want to do 3 partitions: 1 for boot (16MB), 1 for swap (512MB), and the rest for installation.

*what is causing the module failures at the desktop when the live CD does boot that far? is it the time/date setting or is there some other problem that isn't obvious?

*can i precopy all the files onto the hard drive and run the installer from a command-line process somehow? i'm guessing the alternate install CD is the way to do this, but the copy i burned last night wouldn't even boot, so i'm not certain i have that option either.

*are there hardware-specific problems with this computer (i know the ATI Rage 128 graphics is a potential problem) or is the total amount of RAM too small to expect a reliable boot? (the fact that it has booted as far as the desktop twice leads me to think it is capable of running Ubuntu from live CD with the existing hardware.)

any information that people can offer as to how to proceed with this would be really great, especially if you have experience installing Ubuntu on a similar Macintosh. again, please be as specific as you can, especially with regard to terminal commands.

i'm having a hard time just giving up on it and going with Yellow Dog (which a friend has recommended) or another distro, but if i have to i will do that.

thanks in advance for any time people are willing to spend trying to help.

---

### Post by ajmctaggart on 2007-07-20
I cannot answer all your questions, since I too am new to this...

I run a Pismo w/ Ubuntu...couldn't get it installed from this machine though...

I pulled the hd, put it into a newer Tibook and installed from there...you can't do a firewire install due to the yaboot not installing through firewire (known issue)...theoretically if you are savvy enough at the firmware prompt, you can boot manually by pointing to your linux install, but that's too much for me.


I installed by pulling the hd...and if I ever need to now, I just NEVER touch my yaboot partition, and install via target mode and firewire, works like a charm.

You SHOULD BE able to install from disc on a Pismo/Lombard, but I never could...this was the easiest way for me...but if you can get it to work, more power to you...

Also, LiveCd's are known to kinda suck on older mac hardware, just go with the alternate install disk, much easier and this way you can choose to install the yaboot, or just the base Os, etc...

Hope this helps, sorry I am not of more assistance.

Please let us know how it goes!

Good Luck
ajm

---

### Post by radicalspud on 2007-07-24
gave up on ubuntu for now...i'm trying a straight Debian 4.0 text-based install to see if i can at least get the OS up and running.

so far i get past the partitioning and into the install, but it hangs at about 40%. i'm using a potentially faulty hard drive, if i can't get any success after a full re-format i will probably switch to a spare 6 GB drive.

also, i just discovered the netinstall version, which i'm sure is very close to the Debian netinstall i was using last night. i created a CD for that and i'll give it a shot.

if anyone knows how to disable hardware detection with the live-cd boot, i'd appreciate a post or link with that info. i will search for it in other posts, but i'm finding info to be scattered all over and somewhat difficult to find. no surprise i guess. mostly i want to turn off PCMCIA detection and also ACPI or the Mac equivalent of it.\

EDIT: AND i found the PowerPC FAQ page (wiki). hopefully my questions will be answered (mostly) there.

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by radicalspud on 2007-07-28
well, after a number of tries, i finally succeeded using the 6.10 alternate (CLI) install CD. i got the base system and yaboot installed, so i can boot into the command line from the hard drive! woot!

now i just have to figure out how to get the network configured and install the rest.

---

