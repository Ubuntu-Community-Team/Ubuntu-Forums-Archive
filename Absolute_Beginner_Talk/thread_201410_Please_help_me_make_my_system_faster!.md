---
title: "Please help me make my system faster!"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by Jozef on 2006-06-21
I'm still relatively new to Ubuntu (only 3 weeks since installation), but so far I like it.  The only problem is that my system is dreadfully slow, and I'm running out of reading material while waiting for a program to launch.

I've got an AMD-K6 350MHz with 256MB RAM.  Since I don't need all the bells and whistles, I decided to go with Xubuntu and Xfce.  Programs like Mousepad and Thunar are relatively fast - they open within 5-10 seconds, but for Firefox I can take a bathroom break.  Ultimatelly, I'd like to run Open Office, Firefox and Thunderbird, but at the current speed and the related system stability (Xfce has the bad habit of shutting down sometimes) it's not much fun.

Here's what I did so far:
* Checked memory and processor; no problems with either.
* Tried to install the [fglrx](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) driver for my video card.  Failed, and didn't load Xfce until I reset the graphical settings.  In hindsight, this comes as no surprise as the driver doesn't support such old cards as my Ati Rage Pro.
* Installed the 8.25.18 driver.  This one is supposed to be identical to fglrx, but I found the version for video cards built into the motherboards, just like mine.
* Prayed.

I still have the feeling that this slowness is hardware-related, which is why I'm posting my lspci output.  There are two devices that show up as unknown, and searching for them in the forum and Google did not offer a solution on how to make them "known".  I assume that one of the devices may be the sound card, as I'm getting no sound as of now.

Many thanks for your help!

[quote="lspci -v"]0000:00:00.0 Host bridge: ALi Corporation M1541 (rev 04)
        Subsystem: ALi Corporation ALI M1541 Aladdin V/V+ AGP System Controller
        Flags: bus master, slow devsel, latency 32
        Memory at e0000000 (32-bit, non-prefetchable) [size=128M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: ALi Corporation M1541 PCI to AGP Controller (rev 04) (p rog-if 00 [Normal decode])
        Flags: bus master, slow devsel, latency 32
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 00008000-00008fff
        Memory behind bridge: 80400000-804fffff
        Prefetchable memory behind bridge: 80500000-820fffff

0000:00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-i f 10 [OHCI])
        Flags: bus master, medium devsel, latency 32, IRQ 9
        Memory at 82100000 (32-bit, non-prefetchable) [size=4K]

0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV] (r ev b5)
        Subsystem: Unknown device 4341:5245
        Flags: bus master, medium devsel, latency 0

0000:00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev 20) (prog-if 8a [Mast er SecP PriP])
        Subsystem: Unknown device 4341:5245
        Flags: bus master, medium devsel, latency 32, IRQ 14
        I/O ports at 7400 [size=16]

0000:00:14.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet  10/100 (rev 11)
        Subsystem: Linksys: Unknown device 0574
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at 7000 [size=256]
        Memory at 80100000 (32-bit, non-prefetchable) [size=1K]
        Expansion ROM at 80120000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/ 2X (rev 5c) (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Rage Pro Turbo AGP 2X
        Flags: bus master, stepping, medium devsel, latency 32
        Memory at 81000000 (32-bit, prefetchable) [size=16M]
        I/O ports at 8000 [size=256]
        Memory at 80400000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at 80420000 [disabled] [size=128K]
        Capabilities: <available only to root>[/quote]

---

### Post by jvl on 2006-06-21
How much is the system swapping? Do you have a swap partition at all? Maybe adding some memory would help. Post output of the free command please.

---

### Post by localzuk on 2006-06-21
The issue is that Firefox is a cpu and memory hog. Your system is under-spec'd in order to get decent performance out of it. Also, openoffice will be a hugely bloated too. Try a set of tools such as gnumeric, abiword etc... These are much faster.

I don't know too much about thunderbird as I have never tried to run it on a slow pc but it may run slow again.

Another browser you could try which is faster at loading and uses less memory is Opera.

---

### Post by Jozef on 2006-06-21
**jvl:** I dedicated the entire harddisk to Ubuntu, and let the install program have its way with it.  How do I check/increase the swap partition?

**localzuk:** Thanks for the tip!  I've been using Opera on my primary computer since version 5, but since this came with Firefox I assumed the system would be optimized.  As far as Thunderbird is concerned, I'd be happy with PINE for e-mail, but my POP server doesn't want to cooperate.  With OO.o, I was thinking about version 1.x, which is enough to edit/save in MS Office format.  I don't need version 2.

---

### Post by Just4 on 2006-06-21
Well, what would be more helpful is memory and maybe a faster a CPU, K6's run on a socket 7 so you should be able to pick up a good 500Mhz+ CPU for around $8 USD and maybe upgrade to 512MB RAM? - anyways, besides the hardware stuff, if its just for lighter stuff, try as someone suggested is to try some tools like AbiWord, etc, as far as webbrowsers go, have you tried epiphany? its much lighter than Firefox and has the same basic feature set (I use it on my Linux-only PC.) and for e-mail, try Sylpheed its really light.

---

### Post by nalmeth on 2006-06-21
There are a few options for you.

So far, your biggest speed complaint would have to be firefox, correct?
You can try other lighter browsers, swiftfox may be perfect for you, and I think it's built with AMD processors in mind. Automatix can install it for you.

Galeon and epiphany are gnome based browsers, and are lighter than firefox. They use the same rendering engine though, so those may help you out. 

There are a couple of things I like about both browsers in their own way, but I don't find the 16 seconds it takes firefox to open on my laptop too long.
(I'm on 733 Mhz 128 RAM, using open-source ati driver). 

The next biggest problem will be OpenOffice + Thunderbird.

Is there functionality missing from Abiword + Gnumeric for you? I find these apps excellent, because they're fast (not bloated), they look nice, and they can work with .doc and excel files. They may have less functionality than openoffice, but they work like a dream for me.

Sylpheed is a less memory intensive email-suite. It may suit your needs.

Another option that may work for you, before we go too far, is prelinking. I use it on my laptop, and apps open noticably faster. The only drawback is that you have to sit and let it 'prelink' everytime you install any new apps.. Which can take a lot of time. The first prelink takes the longest, if you were to try it I would let it sit overnight. This is not typical behavior, but after a major update when dapper was beta, I once had to leave for 22 hours!! Again, not typical, I had like 200 upgrades which is why it took so long.

If you want to try it the link is here:
[http://www.ubuntuforums.org/showthread.php?t=74197](http://www.ubuntuforums.org/showthread.php?t=74197)

Anything I didn't address feel free to ask again

---

### Post by Jozef on 2006-06-21
Many thanks, guys!  I'm beginning to understand that the problem lies, as is usually the case, between the keyboard and my chair.  I guess I wanted too much from the computer.  Unfortunately, my motherboard doesn't support more than 256MB of RAM (and I already upgraded it - originally it was a Win98 system with 64MB RAM), so I'll stick with my configuration.

I'll give the office programs another try; I guess it's only the interface that I'm not too familiar wiht.  The browser will be crucial, though, as I'll be using this program for some php/mysql software I'm writing (LAMP is already installed and in good order), but because I won't need more than basic HTML and CSS, I can live with an older version of Opera or somesuch.  

Over the course of the past three weeks I've learned quite a lot about the system and how to maintain it; I hope soon I'll stop asking questions and giving answers instead :)

---

### Post by DarthMandeep on 2006-06-22
You say you're working on LAMP stuff, do you actually have Apache and MySQL loaded all the time? Unless this is a production server that's actually talking to client machines, wouldn't it make sense to turn off all that stuff when you're not using it?

If you're going to be reading Slashdot for an hour, why have a web server running during that time?

I'm using a IBM Thinpad 600e as my only laptop. It's got a 366 MHz Pentium 2 and 192 megs of RAM. It works fine with Firefox but I make a point of not running multiple heavy apps at once, and not running any services in the background that I am not using. When I need to print, I turn on CUPS. Then I turn it off. Same thing with other daemons. Since most of my time is spent in Firefox, this is not as big a hassle as it might sound, and Firefox runs more than quickly enough for me. I also use the lightest window manager I can stand to look at, which is JWM. For things that aren't critical to me, like instant messaging and usenet, I use the lightest graphical apps I can, like Ayttm and Sylpheed. 

What programs are running on your machine right now? Which ones are you actually using right now?

---

### Post by jvl on 2006-06-22
[QUOTE=Jozef]**jvl:** I dedicated the entire harddisk to Ubuntu, and let the install program have its way with it.  How do I check/increase the swap partition?

if you type "free" in terminal, you'd see how much swap are you using

In my case: 
$ free
             total       used       free     shared    buffers     cached
Mem:       1003168     965380      37788          0     182664     362332
-/+ buffers/cache:     420384     582784
Swap:      1951736        208    1951528

which means that I have 1GB memory and almost 2GB swap. There are just 208kbytes of swap used.

The reason to check this is to see how much your system uses disk as a virtual memory.

My old computer was P2 @ 350MHz with 256MB RAM. The performance increase after adding another 128MB was noticable.

As it has been already said, the memory footprint could be decreased noticably, if you use alternative applications:

fluxbox or windowmaker instead of KDE or GNOME
opera instead of firefox, or even links -g (always gave me kinda geeky feelings)
mutt or pine instead of thunderbird (or opera mail, while you're at it)
you could tune apache to use smaller number of idle servers, but it would really help to stop apache + mysql when you don't need it.

As a rule of thumb, console applications tend to use much less memory than the graphical alternatives.

Anyways, X are just a way to run lots of xterms in an organized way ;)

HTH

---

