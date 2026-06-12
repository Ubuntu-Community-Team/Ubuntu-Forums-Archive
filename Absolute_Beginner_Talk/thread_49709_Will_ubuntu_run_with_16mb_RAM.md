---
title: "Will ubuntu run with 16mb RAM?"
date: 2005-07-17
forum: Absolute Beginner Talk
---

### Post by ajd344 on 2005-07-17
Hi! I put ubuntu on my computer and there is something wrong with it. The mouse has a big box thing around it and when you move the mouse around it 'paints' the boxes on. Kind of like when you move around the spray paint on mspaint.
The SAME thing happened with knoppix live cd.
The specs are pentium one mmx 166MHz, 160mb ram


SO, I am thinking about putting it on my other computer. This one has: pentium 1 133MHz, **16mb RAM**

Will this run on such old of a computer?

This is my first time with linux, so I need some help.

Thanks

---

### Post by Arthemys on 2005-07-17
My best guess is that it will run, but you won't get to have a GUI because of the low RAM count.

The "painting cursor" issue sounds like a problem with ubuntu not liking your video card all that much. Or just an issue with CPU speed.

---

### Post by ajd344 on 2005-07-17
I am a little confuesed about GUI. Do you mean every program is going to be text based? like:

Type a command below:
|

Will open office open? Or will it be some cheap thing like this:

|FILE| |EDIT| |FORMAT|
Open Office
__________________________________________________



__________________________________________________

How do you tell ubuntu not to boot of GUI?

Thanks,
Andrew

---

### Post by kvidell on 2005-07-17
[QUOTE=ajd344]I am a little confuesed about GUI. Do you mean every program is going to be text based? like:

Type a command below:
|

Will open office open? Or will it be some cheap thing like this:

|FILE| |EDIT| |FORMAT|
Open Office
__________________________________________________



__________________________________________________

How do you tell ubuntu not to boot of GUI?

Thanks,
Andrew[/QUOTE]
 It wont necessarily be text based... but all the graphical stuff might not run too well.
Linux is good at running with little to no system resources available, yes... but X? Not so much.

OpenOffice doesn't have a text only component so it wont open at all.

Not all programs can run in the terminal, only terminal based apps.
Now, that said... a lot of applications that are GUI based do have command line interface (CLI) proponents, and some CLI apps do have Graphical proponents.

You may need to upgrade your system a little to have happy X compatibility, or run a slightly less heavy window/desktop manager than Gnome/KDE like FluxBox or OpenBox.
Of course then you wont have as easy access to all of the graphical tools that make Ubuntu great for new users...

Feel free to post any more questions you have.
- Kev

---

### Post by Arthemys on 2005-07-17
Anything that you would open in GNOME or KDE; such as Firefox or OpenOffice would not launch at all because the system would not be capable of starting the X server.

The xserver is what runs your GUI on your local computer.

Having said that, those programs do not have a non-GUI equivelant. Though there are other programs that do similar things

Internet: Firefox for GUI and lynx for CLI
Text Editing: OpenOffice for GUI and nano or vim for CLI

---

### Post by ajd344 on 2005-07-17
ok... you guys have been very helpful.

I guess i will have to install it on another computer.

Anyway, I think it froze wih RAMDISK: Compressed image found at block 0

I restarted and it did that again.


Thanks, 
Andrew

---

### Post by aysiu on 2005-07-17
Well, on the free CDs I got recently from Ubuntu, this is what it says:
> To use this Install CD, you must have an Intel x86-based computer with at least 32 MB od RAM, and at least 350 MB (for a minimal installation) or 1.8 GB (for a typical installation) free space on your hard drive. Have you considered using Damn Small Linux instead?

---

### Post by ajd344 on 2005-07-17
[QUOTE=aysiu]Well, on the free CDs I got recently from Ubuntu, this is what it says:
 Have you considered using Damn Small Linux instead?[/QUOTE]

Ahh. I have looked a little with that. Is that easy to install?
Unbuntu was very easy for me.

THANKS,
Andrew

---

### Post by kvidell on 2005-07-17
[QUOTE=ajd344]Ahh. I have looked a little with that. Is that easy to install?
Unbuntu was very easy for me.

THANKS,
Andrew[/QUOTE]
 DSL is relatively simple to install...
I would normally recomend Gentoo or Slackware in a system resource situation like this but since you're a new user I think I'll hold off as those would either teach you more about linux than you want to know right now, or scare you away from the OS completely :-P
- Kev

---

### Post by ajd344 on 2005-07-17
Thanks!

Well the old computer (133) doesnt seem to be working with DSL.

So, I tried it with my other computer (166) and it loaded up! I am now off live cd!

Can you make a hard drive install with DSL?

---

### Post by poofyhairguy on 2005-07-17
For the record, the Ubuntu installer requires 32mb of ram.

---

### Post by ajd344 on 2005-07-17
[QUOTE=poofyhairguy]For the record, the Ubuntu installer requires 32mb of ram.[/QUOTE]

Yes, I understand that. I have moved on to DSL.
I am stuck with the install. I got the live cd to work but NOT the hd install. I dont want dual boot. Does anyone know how to create the partition? Do you use MS 98 Boot Disk?

Thanks!

---

### Post by trash on 2005-07-17
I'm not sure why you are having that mouse problem, did you install gnome or kde?

I just installed Hoary on a P1 mmx 166mhz (clocked at 210) with only 98mb of ram and the mouse is smooth (i expected it to be a bit jumpy).
The full Gnome install took 1800mb of my 2800mb drive and that includes a post install upgrade and the automated ubuntusetup script which installed all the extras including java.
Speed isn't even that bad, example, openoffice takes only ~90 seconds to open.
I'm on dsl so even surfing isn't that slow.

maybe try a reinstall as it did take me a few attemptes to get it all right.. wierd ram issue was my problem so i removed all except a 32mb stick for the install and after the install i put the other ram back and everything was good.

---

### Post by ajd344 on 2005-07-17
This happened with knoppix live cd too.

I got DSL to work on my 166mhz computer and would like to make a hd install of that.

I made the partition and copy the files over, but now whenever I want to boot of it, I have to put the cd in and go in through there. I want the BIOS to boot off it.
 Something with booting off dev/hda?

Thanks

---

