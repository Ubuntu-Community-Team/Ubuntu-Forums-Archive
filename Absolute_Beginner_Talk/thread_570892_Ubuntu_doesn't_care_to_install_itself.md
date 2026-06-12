---
title: "Ubuntu doesn't care to install itself"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by Whalefish on 2007-10-08
Hi there.  I've been cruising the forum for a while now and can't seem to come up with an answer for my problem.  Ubuntu simply won't install.  I've tried using the Live CD, the Alternate CD, burning at slow speeds to avoid errors, and tried burning several copies, but no luck.

What happens is this: The GUI loads when I boot up my computer.  I select Install Ubuntu.  Some things get checked, "Kernal is Alive" at the bottom of the screen, waits, blinking cursor at the top...cd spins down...nothing happens.  This occurs with both versions of the CD, and also occurs when I try to check the CD for errors in the menu.

Any idea whats going on? I've read that there are some issues with GeForce 8800 video cards, but the Alternate CD is supposed to clear that up and it didn't.  Any help would be great.

My system specs:
Intel Dual Core 6750 @ 2.66ghz OC'ed
2gb DDR2 RAM
Sony DVD+RW
EVGA Nvidia 8800GTS 320mb
blah blah....

Thanks!

---

### Post by raeb on 2007-10-08
It'd help to know the manu of the motherboard, but as a blank shot in the dark fix, try this.

Reboot and at the gui, press F6 for extra options.  Add this: noacpi to the end of the boot line.  So the line looks like boot ....stuff.tar.gz splash noacpi quiet -- .  Something along those lines.  It's the only way my laptop will boot.

---

### Post by Pumalite on 2007-10-08
Did you do md5sum on iso? Did you burn at 4x? What version of Ubuntu are you installing?

---

### Post by Sef on 2007-10-08
Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the downloads?

---

### Post by Whalefish on 2007-10-08
1. Mobo is an MSI P6N SLI Platinum with the current bios ver

2. md5 checked out just fine

3. Burned at 16x, could that really be too fast?

4. I'm installing 7.04 amd64 alternate (yes i know its 64 bits)

...I'm going to try that command line, but it would be nice if I could get to the root of this problem, and not just work around it.

Thanks for the fast responses so far!

---

### Post by Whalefish on 2007-10-08
Tried the command line, no luck.

Before the system hangs up, the message "Kernal Alive" shows, then below it "Kernel direct mapping tables up to 100000000 @ 8000-d000" and then it just sits there.

My system is quite new, up to date, and in very stable condition.  Not sure why one of the easiest to use distro's of linux won't work.  Not a good sign if linux ever wants to get into the mainstream market.  Last time I tried installing linux a long time ago I wiped out my entire system.  At least that hasn't happened yet :)

---

### Post by Kingsley on 2007-10-08
Try to install the 32-bit version.

---

### Post by Whalefish on 2007-10-08
The 32 bit version actually loaded and got almost to the end of the install, then failed to install Grub.  Someone posted a similar error and they used a different installer and it worked.  I guess that means the alternate cd?

Anyways, 32 bit installer works but 64 bit doesn't.  Anyone know why? My processor and mobo both support 64 bit architecture.

ARGH! Why is Linux so frustrating!?!?

---

### Post by shad0w_walker on 2007-10-08
If i  had to guess the reason it is being awkward for you is the same sort of reason as it was annoying me a few months back.

I have a nice motherboard with an Nforce chipset which originally ended up with slightly wrong specs being released and dodgy BIOS files being installed to the earlier made boards. This caused a problem with Linux access those features. It did exactly this, so if it is the same issue, your problem lies with hardware companies not releasing proper details, not Linux itself, its warning you something is working right.

Anyway, if you can, try updating your Bios (Solved it for me nicely)

---

### Post by k3lt01 on 2007-10-09
I had a similar problem and found that Windows XP was getting in the way. 

I originally started trying to install Feisty but it just wouldn't work. Kept getting memory messages and it would hang and do what you have described. As soon as I formatted the HD (I actually tried to install an old version of RedHat, the install worked but RedHat didn't :confused:)  I tried installing Feisty again and 30 minutes later things were all good.

In my case it didn't work because Windows was on the HD it got in the way as it takes memory.
Try a total reformat of your HD using a Win98 boot disk or something and then try to load Ubuntu. As you have already gone nearly right through an install it couldn't hurt anything.

---

### Post by southernman on 2007-10-09
> **Whalefish said:**
> 

ARGH! Why is Linux so frustrating!?!?
Because it's something your not used to... we've all been there. Besides, GNU/Linux just as Windows or Mac is an inanimate object. Don't let it whip ya.

---

### Post by RayArdia on 2008-02-18
[QUOTE=Whalefish;3499275]Tried the command line, no luck.

Before the system hangs up, the message "Kernal Alive" shows, then below it "Kernel direct mapping tables up to 106000000 @ 8000-d000" and then it just sits there.

My system is also quite new, up to date, and WAS in very stable condition. I've read many posts re "hanging" and unless I can get my wife's laptop working soon I may have to "go to the ablutions" and hang myself!:( 
7.10 hangs in the same way as Whalefish's system. Ubuntu 6.06.1 gets as far as "setting up keyboard" then stops. All I can do then is to switch off.
I'm a beginner at Ubuntu - but have got it (Ver 7.10 32 bit) to run OK on my desktop PC and I would like to use it on my wife's PB laptop.
System:-
PB MX52-B-053D AMD Turion 64x2
ATI Radeon Graphics
Atheros Wireless
1GB RAM, 120GB HDD

---

### Post by RayArdia on 2008-02-19
Have now downloaded what I think is the Alternate CD for Ubuntu 6.06.1. When I select either Install Ubuntu OR Check disk for errors I get:-
1. "Uncompressing Linux....Ok, booting the kernel
2. [17179570.072000  ..MP-BIOS bug: 8254 timer not connected to IO-APIC
Clearly, I'm doing something wrong....but what? Help please.:confused:

Packard Bell Easynote MX52-B-053D
AMD Turionx2
1GB RAM, 120GB HDD
ATI Radeon Graphics
Atheros Wireless

---

