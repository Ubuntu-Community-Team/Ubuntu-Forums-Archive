---
title: "Absolute Install Failure"
date: 2005-07-22
forum: Absolute Beginner Talk
---

### Post by Antinomy on 2005-07-22
Folks,

I been tryin. But it aint been workin!

I have AMD 64 in a Compaq Presario 4000 series, 256 MB RAM, 60 GB HD

I have tried installing Ubuntu (Hoary) twice.

first using x86, as recommended. PROBLEM: This install doesn't seem to recognize my keyboard. At all. I get to splashpage, and key board does not work.


second using 64 install disk. THis one gets halfway through install and says "Debootstrap Error - COuldn't retrieve bsdutils. This may be due to a network problem or a bad CD...burning the CD at a lower speed may help."

Which I did. Down to 8x. Same error when I try again.


Any ideas of how I can get Ubuntu onto my laptop, or is it back to chairman Bill?

Peace,

Antinomy

---

### Post by poofyhairguy on 2005-07-22
[QUOTE=Antinomy]

Any ideas of how I can get Ubuntu onto my laptop, or is it back to chairman Bill?

Peace,

Antinomy[/QUOTE]

Sure. Go to best buy. Get a USB keyboard to get you through the install. Then return the keyboard after its done to get your money back.

If your keyboard doesn't work after the install....its back to Bill I guess.

---

### Post by Jussi Kukkonen on 2005-07-22
[QUOTE=poofyhairguy]Sure. Go to best buy. Get a USB keyboard to get you through the install. Then return the keyboard after its done to get your money back.[/QUOTE]
 If I recall correctly this won't work -- usb keyboard is not usable in the beginning of the installation...

---

### Post by poofyhairguy on 2005-07-22
[QUOTE=Jussi Kukkonen]If I recall correctly this won't work -- usb keyboard is not usable in the beginning of the installation...[/QUOTE]

Really? Damn...then I don't know....

---

### Post by WirelessMike on 2005-07-22
No ps2 at all on that compaq?  i mean--  you could always get a usb to ps2 adapter or a cheap standard ps2 keyboard as long as the compaq mobo has ps2 ports out the back...

---

### Post by Antinomy on 2005-07-22
[QUOTE=WirelessMike]No ps2 at all on that compaq?  i mean--  you could always get a usb to ps2 adapter or a cheap standard ps2 keyboard as long as the compaq mobo has ps2 ports out the back...[/QUOTE]
 Ok, I like this. I use an external KB, which I have.  Once I'm in to the system, what do I do to get it to recognize the original laptop keyboard? Is there a setting I can change somewhere?

Thanks for the patience guys, I want to stay with Ubuntu - it's running like a dream on my desktop, I really really love it (and I'm learning a ton too...)

Antinomy

---

### Post by poofyhairguy on 2005-07-22
[QUOTE=Antinomy]Ok, I like this. I use an external KB, which I have.  Once I'm in to the system, what do I do to get it to recognize the original laptop keyboard? Is there a setting I can change somewhere?
[/QUOTE]

Yep...we have ways to try to get it to work once installed.

---

### Post by Antinomy on 2005-07-22
awesome. Moving ahead! Will report back tonight

---

### Post by Antinomy on 2005-07-23
Ok!

Progress: I got through to the GUI with help from my friend Nalioth.  He showed me how to reconfigure so the monitor doesn't crash the system. Very cool.

So, three things remain:

1)Touch pad mouse doesn't work/isn't recognized
2) Built-in KB doesnt work (both mouse and KB  commands are going through USB now)
3) Fulll monitor support (least of my worries)

So, starting with the KB. I went into the config under preferences and chose the compaq laptop version. This still doesn't work....any ideas? I guess this is the first thing to tackle...an external KB is much clumsier than an external mouse!

THanks in advance for your input,

ANtinomy

---

### Post by poofyhairguy on 2005-07-23
Ok...they best way would be to use this command:

sudo dpkg-reconfigure xserver-xorg


in a regular terminal. Keep trying different keyboard settings and see if one works.

---

