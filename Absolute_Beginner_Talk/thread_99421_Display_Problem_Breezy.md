---
title: "Display Problem Breezy"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by Telchar on 2005-12-05
Hi all,
Just wanted to give ubuntu a try since I had problems configuring my wireless in Mepis. Im reeeally new to the whole linux thing...
So i try the live 5.10 ISO. The part of the install that is text based works fine, [COLOR="Red"]but when the GUI loads all I see is the mouse pointer and horizontal lines across the whole screen.[/COLOR] White, brown and black repeat their way from top to bottom. I cant access any menu and it doesn't matter what rez I'm using, exept if i try to boot at the lowest possible (480x640?), then its all garbled in pink instead...
I have an NF2 AthlonXP 3000+ Geforce6800 system. It does the same thing on both my TFT (well known brand ;-) (not!)"Topvision" 18") and my 19" sammy CRT.
would love to give more detail, but as said, I cant access anything once "in".

Any Ideas? Can I Halt the live cd boot somehow and access some command that will let me experiment with resolutions and frequencies?

Also, Can I install Ubuntu with the Live CD? Or do I have to d/l the non live version? (in Mepis it was All-in-one)

feels kinda abrupt to have to end it here!   Anyone??

---

### Post by endersshadow on 2005-12-05
You'll have to d/l the non live version to install.

Try running this command in the command line:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Telchar on 2005-12-05
[QUOTE=endersshadow]You'll have to d/l the non live version to install.

Try running this command in the command line:

```
sudo dpkg-reconfigure xserver-xorg
```[/QUOTE]


Ok. So the non live version will let me specify stuff the live version doesn't? I thougt they were the same?

Ohwell...I wonder if working out the wireless issue in Mepis or triple booting (mepis already dualboots) is easier with a fairly severe ubuntu graphics issue. sigh.
thank you for the input tho, appreciate it.

any OTHER suggestions are MOST welcome!! ;)

---

### Post by Telchar on 2005-12-06
ok...bump.
Ill give the full install a try later tonight. But in the meantime...

[COLOR="Red"]Anyone knows whats causing the horizontal lines i described on the display?[/COLOR]
I was guessing my display wasn't supported, but since both displays showed the same thing...thats not it. Isn't my GF6800GT 256MB ASUS supported? 

Gave the Live CD a try in my Dell XPS2 as well, worked like a charm.
Too bad I need it for work...

---

### Post by Telchar on 2005-12-06
ok, here we go again.
I have installed Ubuntu. Triple boot with winxp and mepis. Im actually rather proud...Everything in ubuntu looks the same tho. I can see the mouse pointer (even with shadow!) but nothing else useful. No response to keystrokes, can't bring up terminal och ctrl-alt-backspace...nothing. I can move the mouse around but no response from clicking anywhere.

I Really need some help.
Top Question. Why is it like this?

followed by...
Where can i type the reconfigure command?
Is it someplace before the "GUI" loads up?
if so, how do i quit safely? Can i hard reset like in windows?

Ill try to attach some shots of my monitor.

[ATTACH]4201[/ATTACH]

[ATTACH]4202[/ATTACH]

pleeeease help

---

### Post by jwd45244 on 2005-12-06
Pick the failsafe mode from the GRUB menu

---

### Post by Telchar on 2005-12-06
Can i hard reboot (reset button) to get there?

---

### Post by jwd45244 on 2005-12-06
Yep

---

### Post by Telchar on 2005-12-06
I suppose it often gets worse before it gets better. I ran thru the xserver reconfigure.
Now i cant even load the GUI.

The one hitch I found was typing the horizontal and vertical refresh, the program wouldn't let me erase all the old numbers. The leftmost figure was impossible to reach, same thing when it wanted me to name the monitor profile...

I might get tired of this real soon. sigh. i wanted this to work.
monitor manual [here]("http://www.planar.com/Products/docs/CBU/archive_manual/Manual-PT1814NUV.pdf")

IF its even got ANYTHING to do with the monitor...

---

