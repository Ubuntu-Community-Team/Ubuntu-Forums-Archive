---
title: "Anyone got Ubuntu on an external USB drive to work?"
date: 2007-04-12
forum: Apple Intel Users
---

### Post by xGuse on 2007-04-12
I have 6.10 installed onto a western digi 60G USB2 drive.  When I boot, rEFIt shows my good ol reliable OSX, a Legacy OS on HD (i assume its my WD USB), and then a Linux on HD (which i ALSO think is my WD USB).  ????

->When i try to boot the linux HD i get "Missing Operating System".
->When i try to boot the "legacy OS" HD I get a screen with a lot of errors that i seem to have forgotten.

In both cases the screen is frozen and i have to power down to continue.  Has anyone figured out how to get around this issue?!  I am BURNING up to get onto Ubuntu!

Thanks for your patience.

Gus

---

### Post by ronocdh on 2007-04-13
I know it's obviously not what you want, but I have to encourage you to do a genuine hard drive install. You don't need nearly as much space as you'd probably think... for example, on my 120GB MacBook Pro HD, I believe I have my Ubuntu partition to 5GB or something. I don't need larger because I can access all my media and documents across all my partitions (I also have Win XP installed).

I highly encourage you to pursue this route! And if you're still not interested, well, here's a bump for ya. ;)

---

### Post by xGuse on 2007-04-13
You are telling me something that has been in the back of my head for a while but i just didnt want to give in to.  Ok so you seem to manage with your 120 G HD; I should be able to with mine.  The only thing is setting it up so i can share files.  Can you recommend a thread or a tutorial that will help me through setting that up?

Also did you use bootcamp?

Thanks for the thoughts.

Gus

---

### Post by ronocdh on 2007-04-13
> **xGuse said:**
> You are telling me something that has been in the back of my head for a while but i just didnt want to give in to.  Ok so you seem to manage with your 120 G HD; I should be able to with mine.  The only thing is setting it up so i can share files.  Can you recommend a thread or a tutorial that will help me through setting that up?

Also did you use bootcamp?

Thanks for the thoughts.

Gus

I did not use Boot Camp. I actually triple boot my system, as I mentioned above, so I partitioned my drive using the **diskutil** command in the terminal (in OS X). If you are just looking to dual boot between OS X and Ubuntu, I recommend [this guide]("https://help.ubuntu.com/community/MacBook").

It is for MacBooks and not the MacBook Pro, but it has a godsent shortcut that lets you use GRUB instead of LILO. I actually used the kludge even to triple boot, for those who are interested. If triple booting is more your thing, try [this one]("http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu") or [this one]("http://ubuntuforums.org/showthread.php?t=198453").

Remember, you don't **have** to use LILO, but it does give slightly better functionality, at the cost of extra setup. (If you use GRUB, you have to choose Ubuntu twice essentially, on two consecutive screens. Big whoop, I say!)

Post again with any more questions, and best of luck to you!

---

### Post by xGuse on 2007-04-14
> To make GRUB installation work, GPT and MBR must be in sync and the boot partition must be of type Linux. Thanks to Debian's [WWW] refit package, available in its unstable repository, GPT and MBR can be synced from within Ubuntu. After partitioning the Macintosh HD, but before installing GRUB, syncing must be done and the boot partition type must be set to Linux. (Since the installer always repartitions the disk automatically, breaking GPT/MBR sync, fixing the disk before starting the installation doesn't work!)

uhhh...  What if i have rEFIt installed in OSX?  will this break the install?  Should i uninstall it and then re-install it from the LiveCD?

Thanks.

Gus

---

### Post by ronocdh on 2007-04-14
> **xGuse said:**
> uhhh...  What if i have rEFIt installed in OSX?  will this break the install?  Should i uninstall it and then re-install it from the LiveCD?

Thanks.

Gus

I also use rEFIt. What I meant by having to "choose Ubuntu on two consecutive screens" was that by using the GRUB method instead of LILO, you'll have to choose Linux from the rEFIt menu, and then you'll be taken to the GRUB menu. Hit Ubuntu again. Boom, done. If you are triple booting, meaning you also have Windows installed, choosing Linux **or** Windows from the rEFIt menu will still take you to GRUB; on the GRUB screen, select either Ubuntu or WinXP.

Much luck!

---

### Post by Chrisj303 on 2007-04-14
I use LILO for my tripleboot, and have had no problems whatsoever - GRUB was nothing but a pain in the ****, It only responds to the keyboard 20% of the time and it's BUTT UGLY! Installing LILO is a snap, and it is just as easy to configure as GRUB.


303

---

### Post by ronocdh on 2007-04-15
> **Chrisj303 said:**
> I use LILO for my tripleboot, and have had no problems whatsoever - GRUB was nothing but a pain in the ****, It only responds to the keyboard 20% of the time and it's BUTT UGLY! Installing LILO is a snap, and it is just as easy to configure as GRUB.


303

Maybe for some. I concur that GRUB is butt ugly, but getting LILO up and running was a bitch on my C2D MBP. =/ So much so that I caved and took the easy way out and kludged the GRUB setup. Looking forward to Feisty solving this!

---

