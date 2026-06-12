---
title: "question about wine, printing and bootloader"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by ltho on 2008-03-04
is there any way to configure the ubuntu 7.10 default bootloader?? is there a visual way to do it?? ( not using command line. i hate command line)

wine is not running on my system. i install it by synaptec. any time i try wineconfig, the system just freeze (no mouse activity, the clock stop).

i also trying to do double-side printing, which does not seem to be supported. now i have to try to print right side and then lelf side separately, which is quite tedious. besides, is there any progarm that allow me to print on the cd printable surface. i try glabel, but not sure how it work.

my system: sempron2400+, 512 mb ram, 350mb swap, 3gb ext3 for the ubuntu partion, with 800mb free, vga onboard. printer:epson stylus R210

---

### Post by smartboyathome on 2008-03-04
A) You can use StartUp Manager to configure it.
B) Try going to winehq.org and using the instructions to use their repo.
C) There currently isn't one. You would have to talk to the people who make the drivers for your printer to see if they can make an option to support dual-sided printing.

---

### Post by JoshuaRL on 2008-03-04
Okay, I think I might be able to help on the first two.

Could you explain more what you want, what is wrong, and any ideas you have for what you're trying?

For wine, I would suggest you get it directly from them.  You're sure to have the newest stable version of Wine that way.First, uninstall wine from synaptic.  Then, we'll do three steps.  Unfortunately this will require a little work from the terminal.  This will be strictly cut-and-paste stuff though.  And we'll go in easy steps.  The terminal is a little daunting at first, but its really powerful and once you get used to it you'll love it.

First of all, these are [taken from here.](http://www.winehq.org/site/download-deb)

1).  get the APT key by putting this the terminal:
```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

```

2).  add the Wine repository to your software sources:
```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list

```

3).  then, update APT and install wine:
```

sudo apt-get update
sudo apt-get install wine

```

That will install the newest version of Wine, and then you can go into Applications->Wine->Wine Config to configure Wine.

---

### Post by ltho on 2008-03-05
i m sorry, but where can i find star up manage??

---

### Post by JoshuaRL on 2008-03-06
> **smartboyathome said:**
> A) You can use StartUp Manager to configure it.
B) Try going to winehq.org and using the instructions to use their repo.
C) There currently isn't one. You would have to talk to the people who make the drivers for your printer to see if they can make an option to support dual-sided printing.

Sweet, didn't know about the StartUp Manager

> **ltho said:**
> i m sorry, but where can i find star up manage??

Go to Applications->Add/Remove.  Then search for "startup manager".  Install that package, it will allow you to fix what you want.

---

### Post by ltho on 2008-03-07
sorroy, i thought the startup manager is installed by default.
about wine, they say because it run in user mode, it shouldnt freeze my mouse and every thing. they suggest i check my system. do you know any one who have the same problem??
by the way, amarok isnt playing from cd. i already install pyron cddb, but that doesnt help much.

---

