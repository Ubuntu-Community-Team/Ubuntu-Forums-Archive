---
title: "Several questions"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by someonedumb on 2006-09-21
Hi, I installed Ubuntu this week and have been able to get it to do exactly zero usefull things so far, here are some specific questions.

Networking:
1. LAN networks - How do you set up the network adapter to use IPv4 (for some reason my network adapter defaulted to installing *only* IPv6... but I'd like to be able to talk to LANs as they exist today, not the future)

2. Dial up - Ok, this one is driving me nuts... When I configure the dial up adapter (using the GUI) and click 'activate' it properly dials the number, but once it connects to the ISP it sits there idly for about 15 seconds and disconnects with no error message and without updating the GUI to reflect that the connection is no longer active. Also about 50% of the time when I open the GUI it loses all the settings and I have to re-enter them all from scratch.

Bash:
1. mount - I want to mount my second HD (the one windows runs on). It is fat32, so do I use the '-t vat32' option? Also, there is no 'hdb' in /dev as I would expect... how do I get linux to recognize the HD exists? (It is physically plugged into the secondary IDE channel)

2. gcc - Why doesn't ubuntu come with gcc?

Device Drivers:
How do you install/uninstall drivers? By default Ubuntu installed two video card drivers (according to the GUI device manager) when I only have one video card, and I'd like to remove the redundant one.

---

### Post by someonedumb on 2006-09-21
Bumping rq... Also, I dont expect replies to anser all the questions, an answer to just one would be wonderfull :P

---

### Post by kidders on 2006-09-21
Hi there,

> How do you set up the network adapter to use IPv4
It's quite tricky to remove support for IPv4 from your system ... how have you determined it's not there?

Incidentally, all modern LANs are capable of using IPv6 exclusively, if you happened to want to do things that way.

> once it connects to the ISP it sits there idly for about 15 seconds and disconnects with no error message
Sounds like some kind of a timeout ... check your ISP's website to make sure you have all the connection parameters right.
 
> I want to mount my second HD (the one windows runs on).
There is no "vat32" parameter for the "-t" option. Check the man page for mount for a list of supported filesystems. Try **sudo mount /dev/hdb1 /mnt/windoze** or **sudo mount -t vfat /dev/hdb1 /mnt/windoze**.

> there is no 'hdb' in /dev as I would expect
Check your dmesg for messages about detected hard drives. If your disk is a secondary slave, it might be called /dev/hdc ... just in case.

> Why doesn't ubuntu come with gcc?
I imagine Ubuntu's devs consider it unlikely that the average home user will have any need for it. You can "apt-get install" it with a single command, however.


> Ubuntu installed two video card drivers (according to the GUI device manager) when I only have one video card, and I'd like to remove the redundant one.
Could you post your xorg.conf and maybe an lsmod, so we can see what you're referring to exactly?

---

### Post by someonedumb on 2006-09-21
Thanks for the reply :D

Upon further testing it appears IPv4 is working (can set a static IP address and ping it).

I was using the default GUI windows for dial up, the few options it allowed me to specify were correct, what type of program is usually used for dial up? Do people typically use a command line program for dial up?

I feel silly about my 'mount' question.. forgot to put the '/dev/' in front of 'hd?'.

The command "apt-get install gcc" resulted in the error "Package gcc has no installation candidate". So do I need to download it? Or is there a different compiler I should look for locally?

I checked xorg.conf and there were no duplicate entries, apparently the duplicate video card driver is an artifact of the GUI "device manager".

I think I learned to not trust the GUI stuff, two of my problems (IPv4 and video card) were caused by the GUI telling me something incorrectly, and thus were not actual problems.

---

### Post by Sef on 2006-09-21
> The command "apt-get install gcc" resulted in the error "Package gcc has no installation candidate". So do I need to download it? Or is there a different compiler I should look for locally?

Do this to download it:

Sudo aptitude update

sudo aptitude install build-essential

GCC is included in it.

---

### Post by kidders on 2006-09-21
> I feel silly about my 'mount' question.. forgot to put the '/dev/' in front of 'hd?' Easily done!

**Edit:** GCC issue answered far better by Sef! Removed.

> I think I learned to not trust the GUI stuff, two of my problems (IPv4 and video card) were caused by the GUI telling me something incorrectly, and thus were not actual problems.
Yeah, it is waaay to easy to configure GUI-based apps to do things that are a little weird.

I'm a bit fuzzy on modem configuration I'm afraid ... it's been years and years since I've used one. I would suggest taking a peek at what's going on from the command line. Also, be aware that negotiating a dial-up connection takes place in "stages". Knowing which stage the failure occurs at would be half the battle :-)

---

### Post by someonedumb on 2006-09-21
Ok I stumbled across a command line dial up program called wvdial. Configured it and it dialed the number etc, and then gave this output:

Carrier detected waiting for prompt.
Connected, but carrier signal lost! Retrying...

It then got into a little endless loop of initializing and de-initializing the modem lol.

Thanks for the above replies btw :D

---

### Post by someonedumb on 2006-09-21
I just used a third piece of software (pppd) to dial up, and the same thing happened, after dialing and negotiating (making all the buzzing and beeping) it disconnects. I'm starting to think its a driver problem, since all three software packages acted the same way. Is this a reasonable conclusion?

---

### Post by Metacarpal on 2006-09-21
> **someonedumb said:**
> I just used a third piece of software (pppd) to dial up, and the same thing happened, after dialing and negotiating (making all the buzzing and beeping) it disconnects. I'm starting to think its a driver problem, since all three software packages acted the same way. Is this a reasonable conclusion?

Possibly, though I also wouldn't rule out phone-line interference.  Can you try another cord to go from your computer to your wall jack?  Also, if there is another device (such as a telephone or answering machine) or a line-splitter between your computer and the wall jack, disconnect from that and plug your computer's modem/phone line directly into the wall (unless you're running the phone line through a fancy surge protector - that's okay to keep!)

Often, it's something simple like that.  Just thought you might want to check it first before you spend three hours trying to fix a driver that might not be broken.

---

### Post by kidders on 2006-09-21
I don't think so ... all modern modems use the same command set, really. "Carrier lost" means the remote host got fed up waiting for you to do something, and dumped you. Now if only we could figure out what that is!

pppd is the thing to work with imho ... everything else is probably just an interface that sits on top of it. You should check that you're using the correct protocols (SLIP, CHAP, etc.) I'll try to think of something smarter to say, and post back hehe.

---

### Post by kidders on 2006-09-21
> **Metacarpal said:**
> Possibly, though I also wouldn't rule out phone-line interference.

Good point!

---

