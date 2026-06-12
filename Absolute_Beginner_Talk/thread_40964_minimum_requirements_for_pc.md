---
title: "minimum requirements for pc"
date: 2005-06-11
forum: Absolute Beginner Talk
---

### Post by truaim on 2005-06-11
Hi im new to ubuntu/linux. I installed ubuntu on a hp laptop:550hz 64mb ram 4 gig hd and it is SLOW, it just barely turns over. I thougt that linux would take less of this pc than say win? But just opening task manager in ubuntu takes over 20 megs??
Is this right or do i need to do some adjustments?
Thanks ](*,)

---

### Post by az on 2005-06-11
Ubuntu usually runs faster than Windows XP.

You have a small amount of ram and would feel a big performance improvement by adding more ram.

A 550 MHz system should not be _that_ slow.  Perhaps you are experiencing some configuration issues?  Does your cpu run at 100 percent all the time?

Insofar as memory management, well you system will run faster if more memory is used.  The fact that opening an app consumes a lot of memory does not mean much in itself.  The kernel caches as much stuff as it can to improve performance.

Much of what is in memory are shared libraried.

If everyting is fine and you just want a faster system, you can either just add some ram, or you can install a lighter desktop environment.  Try icewm (install the menu package, too) or XFCE4 (both in universe)

I would recommend a lighter environment for a computer with less than a 400 MHz CPU.

---

### Post by heltinde on 2005-06-11
I have PIII 600 mhz and 256 MB ram on my box. It runs very nice! I've tried with 128 first, it works OK, but I really felt a difference when I added another 128 block.

---

### Post by aysiu on 2005-06-11
64 MB of RAM is too small even for most Linux distributions; though, setting up a SWAP partition might help (one of equal size--64 MB). You're not looking for Ubuntu. You're looking for something like Damn Small Linux, Puppy Linux, or Feather Linux.

---

### Post by gil-galad on 2005-06-11
Yup, its the ram.  Gnome really needs about 256mb to run smoothly.

---

### Post by az on 2005-06-11
[QUOTE=gil-galad]Yup, its the ram.  Gnome really needs about 256mb to run smoothly.[/QUOTE]

I would say the threshold is more at the 128 meg level, with a slightly better performace with more and more ram...

And as far as swap, there probably already is a swap.  That does not speed up your system, though.  It just makes it more stable....

Swapping is bad.  That is why things suddenly get so slow.  You start swapping and your system starts to crawl.  That is better than X shutting down, though.

---

### Post by aysiu on 2005-06-11
Why is swapping bad? I installed Mepis on my friend's 128 MB RAM computer with 128 MB swap, and it ran significantly faster with the swap.

---

### Post by poofyhairguy on 2005-06-11
[QUOTE=aysiu]Why is swapping bad? I installed Mepis on my friend's 128 MB RAM computer with 128 MB swap, and it ran significantly faster with the swap.[/QUOTE]

Because what "swapping" is is when you borrow some hard disk space to work as RAM because your RAM is full. It is ALWAYS slower than the main RAM because RAM is a LOT faster than harddisk (harddisks are the biggest bottleneck on a modern computer). If your friends ran faster it wasn't because of swap- swap was something else that was a part of another solution I bet.

---

### Post by poofyhairguy on 2005-06-11
[QUOTE=truaim] I thougt that linux would take less of this pc than say win? [/QUOTE]

That is true. Its just that Linux is very diverse. Some versions of Linux (say Feather or Damn Small Linux) uses a less nice desktop environment and uses WAY less resources than Windows. Ubuntu (which uses Gnome) is a top end version of Linux that is meant to be modern and competitive with OSX and XP as far as features/looks go. Our version of Linux is NOT meant to save old machines that are too weak for Windows. It meant to be a replacement for newer systems that can run Windows fine.

Your computer will run Ubuntu fine if you can find some way to get 256+mb of RAM in it. I have a system with a weaker CPU than that computer loves Ubuntu because it has 256mb of RAM. You can't run the newest and shiniest OS on old hardware without some upgrading I'm afraid. Please note that buying the RAM might be the best option- versions of Linux made to run on 64mb of RAM do NOT have desktops that are competitive with Windows when it comes to features.

---

### Post by poofyhairguy on 2005-06-11
[QUOTE=azz]I would say the threshold is more at the 128 meg level, with a slightly better performace with more and more ram...
[/QUOTE]

Yep, I'd say 128mb should be considered to be minimum. Gnome can't relax until it has 256 though.

---

### Post by aysiu on 2005-06-11
[QUOTE=poofyhairguy]Because what "swapping" is is when you borrow some hard disk space to work as RAM because your RAM is full. It is ALWAYS slower than the main RAM because RAM is a LOT faster than harddisk (harddisks are the biggest bottleneck on a modern computer). If your friends ran faster it wasn't because of swap- swap was something else that was a part of another solution I bet.[/QUOTE]

I disagree. Mepis comes with a meter that shows how much memory and how much swap and CPU is being used at any given time. Swap was always being used in addition to memory (about 64% of memory and 50% of swap).

---

### Post by truaim on 2005-06-11
Thanks, the reason i installed it on the laptop with only 64mb ram is that i wanted to test it out before i installed it on my stationary pc, wich is alot faster.

Asus P4P800se
P4 3,0 
1024 mb ddr ram
160+200 gig sata hd
radeon 9600pro 256
water cooled

---

### Post by az on 2005-06-11
I run Debian and Ubuntu on a variety of low-end systems and the swap is always zero.  If it is used, it is only transient.

Does mepis use an old 2.4 kernel?

---

### Post by poofyhairguy on 2005-06-11
[QUOTE=truaim]
Asus P4P800se
P4 3,0 
1024 mb ddr ram
160+200 gig sata hd
radeon 9600pro 256
water cooled[/QUOTE]

The ATI driver might give you a little trouble, but otherwise that machine is more than enough for Ubuntu.

---

### Post by aysiu on 2005-06-12
[QUOTE=azz]I run Debian and Ubuntu on a variety of low-end systems and the swap is always zero.  If it is used, it is only transient.

Does mepis use an old 2.4 kernel?[/QUOTE]

Mepis gives you the option to use 2.4 or 2.6. I was using 2.6 on my friend's and the swap was constantly in use. Really, creating that swap partition was the only way I could get the live CD to operate at a reasonable speed (I used Mandrake to create the swap partition). On my computer (512 MB RAM), the swap is always 0%.

---

### Post by keithpeter on 2005-06-12
[QUOTE=poofyhairguy]Yep, I'd say 128mb should be considered to be minimum. Gnome can't relax until it has 256 though.[/QUOTE]

Does anyone know what is happening about the following proposal for Breezy?

[http://udu.wiki.ubuntu.com/LightweightDesktop?highlight=%28DistroSpec%29](http://udu.wiki.ubuntu.com/LightweightDesktop?highlight=%28DistroSpec%29)

Such a 'low weight' option for installation from a standard Ubuntu intstaller CD-ROM would help all of us to make use of 'attic ware' computers, thus helping the environment  O:)

---

### Post by az on 2005-06-12
[QUOTE=aysiu]Mepis gives you the option to use 2.4 or 2.6. I was using 2.6 on my friend's and the swap was constantly in use. Really, creating that swap partition was the only way I could get the live CD to operate at a reasonable speed (I used Mandrake to create the swap partition). On my computer (512 MB RAM), the swap is always 0%.[/QUOTE]


You are referring to a live cd.  This is not what I am talking about.

Could the things on the /home ramdisk be swapped preferentially on Mepis?

That sounds like a question for Jdong.

---

### Post by az on 2005-06-12
[QUOTE=keithpeter]Does anyone know what is happening about the following proposal for Breezy?

[http://udu.wiki.ubuntu.com/LightweightDesktop?highlight=%28DistroSpec%29](http://udu.wiki.ubuntu.com/LightweightDesktop?highlight=%28DistroSpec%29)

Such a 'low weight' option for installation from a standard Ubuntu intstaller CD-ROM would help all of us to make use of 'attic ware' computers, thus helping the environment  O:)[/QUOTE]


I was considering jumping in on this.  I started to look for an email address for the lead member of the team but have not found it yet...  Perhaps we should ask on Ubuntu-devel?

---

### Post by keithpeter on 2005-06-12
[QUOTE=azz]I was considering jumping in on this.  I started to look for an email address for the lead member of the team but have not found it yet...  Perhaps we should ask on Ubuntu-devel?[/QUOTE]

[email]colin.a@gmail.com[/email] found on [http://edubuntu.org/](http://edubuntu.org/) - another project I'm interesting in watching.

I posted on Breezy Release forum.

---

### Post by az on 2005-06-12
[QUOTE=keithpeter][email]colin.a@gmail.com[/email] found on [http://edubuntu.org/](http://edubuntu.org/) - another project I'm interesting in watching.

I posted on Breezy Release forum.[/QUOTE]


The Ubuntu-devel mailing list would be better.  

Thanks for the address.  I will email him.  The project seems to be dependant on edubuntu progress.

---

### Post by served on 2005-06-25
But i have 126mb ram and 8gb HDD and AMD K6-2 450 mhz CPU
But i have a problem with memory. I'd like to free some but how can i turn services off and make gnome to take less memory?

---

### Post by musicman2059 on 2005-06-25
[QUOTE=served]But i have 126mb ram and 8gb HDD and AMD K6-2 450 mhz CPU
But i have a problem with memory. I'd like to free some but how can i turn services off and make gnome to take less memory?[/QUOTE]
 It's interesting, actually.  I'm runing my computer on a Cyrix II 366 MHz with 192 MB RAM.  (It's OLD!)  I'm finding that, even with GNOME up and running and such, I still have around half my memory, so I'm not really sure where this 256MB figure came up.

However, I'm noticing that most user-induced processes shoot up the CPU to 100% while being used, and in some cases, (up to something as simple as adding a space into a large file in Bluefish) shoots my CPU up to 100%.  I'm assuming the problem is because of my very slow CPU speed, but what else is new? :P

---

### Post by poofyhairguy on 2005-06-26
[QUOTE=served] I'd like to free some but how can i turn services off and make gnome to take less memory?[/QUOTE]

Impossible. The best you can do is to use xfce.

---

### Post by dutch_boi1 on 2005-06-30
hey everyone i am new 2 ubuntu and have had some problems with it. the problem that i am having is that after i install it (to a 10gb hardrive) , and i reboot , it tries to load the graphical user interface, but ti cant , so basicly i am left with something that looks like dos. i have tried reinstalling it but it duznt work. my computer has an intel celeron 2.8ghz processor with 768 mb of ram. i have everything else which should b working with this. i ordered  the cd from the website and i got the cd, it is an original version. it is the intel x86 version.could someone plz tell me what x86 computer means? .i have read the system requirements and i go ay past those. could someone plz help me becauz i really want my comp back up again. ](*,)

---

### Post by Potemkin on 2005-07-01
[QUOTE=poofyhairguy]Impossible. The best you can do is to use xfce.[/QUOTE]
Not quite. You can improve the performance of Gnome and make it use less RAM by getting rid of Nautilus and using Rox-filer to draw your desktop and browse your file system. Do 'apt-get remove nautilus' and 'apt-get install rox-filer', then go to System->Preferences->Sessions. Click on the 'Startup Programs' tab and the 'Add' button. Add the command 'rox --pinboard=MyPinboard' with order '50'. Save and restart Gnome. The bloated and RAM-hungry Nautilus has now been replaced with the lean and fast Rox-filer.

---

### Post by picpak on 2005-07-01
1) Replace the theme to Simple, and the Window Border to Atlanta.
2) Remove all the special effects from Nautilus.
3) Remove as much from the gnome-panel as you can. Try combining it into one panel.
4) Use lighter programs. [Lo-Fat Linux](http://users.netwit.net.au/~pursang/lofat.html) is a good start.
5) Reduce your swappiness to 10, and disable some mingetties. Read how [here](http://www.linuxjournal.com/article/8308).
6) Use a program lighter than OpenOffice, like AbiWord, or if you have the money, TextMaker. There's also a tutorial to speed up OpenOffice in the same link.
7) Enable DMA, and set 32-Bit IO-Support. This will speed up your hard drive. Read how [here](http://www.linuxjournal.com/article/8317).

That's about it :)

---

