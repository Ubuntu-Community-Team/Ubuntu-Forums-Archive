---
title: "Powermac G5 Yaboot Issues"
date: 2015-10-23
forum: Apple Hardware Users
---

### Post by wamjones99 on 2015-10-23
Hi all,

I have a Powermac G5 that I've been trying to use as a linux box, and I've been having some major problems.

Firstly, I tried installing Debian, which seemed to install fine, but once I tried using it, the entire screen was tinted green. I presumed that it could be something to do with the fact that I used an adapter to change the DVI output to a VGA cable.

After that I tried installing Ubuntu, which wrecked everything. All I get is a black screen that only says something about yaboot.

So I was just wondering if anyone else has had a similar  experience with similar hardware.

Thanks,

Will

---

### Post by howefield on 2015-10-24
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by este.el.paz on 2015-10-29
> **wamjones99 said:**
> Hi all,
I have a Powermac G5 that I've been trying to use as a linux box, and I've been having some major problems.
Firstly, I tried installing Debian, which seemed to install fine, but once I tried using it, the entire screen was tinted green. I presumed that it could be something to do with the fact that I used an adapter to change the DVI output to a VGA cable.
After that I tried installing Ubuntu, which wrecked everything. All I get is a black screen that only says something about yaboot.
So I was just wondering if anyone else has had a similar  experience with similar hardware.
Thanks,

Will

Will:

There are apparently some issues that crop up on the G5, I don't have one, but there are threads here about them if you search Google and then look for the hits that show up from this sub-forum.  However, I do have experience with G4 machines, and the issues you describe generally relate to the xorg.conf file and getting that properly set up for your computer.  You can find much of this on the PowerPCFAQ wiki.  If you can see the flashing boot prompt on the yaboot screen you can try to add some boot parameters to see if that gets you passed the black screen.  Also, can you boot into a TTY and see the command line interface?

You haven't listed the system that you are trying to install, generally the ***easiest*** PPC install is with some 12.04 flavor.

e...

---

