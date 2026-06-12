---
title: "newer than n00b..."
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by finwhiz on 2006-04-04
Hello all,
I am an absolute newbie to Ubuntu. I am trying to intall it and I cannot. My problem is so basic that I searched for it in the forum but could not find a solution to it... this is my problem:
I burnt the ISO in a CD, and then... I do not know what to do. I restart my computer (a dell optiplex GX280) with the CD in the tray and nothing happens, ie, windows starts again. I cannot find an .exe file in the CD to run from windows either.
So, what do I do now?? 
Thanks a lot and please excuse the stupidity of my question.

---

### Post by Sef on 2006-04-04
Solutions:

1) You need to set the boot order to check the cd rom first.  a) If your BIOS has a one-time boot hit that (F12 on my Dell.) B) if not, then go into the boot and change the order (F2 on the Dell.)

(Most often to get into the boot, you press either esc, delete, F2, or other.  It will tell you when you boot up.)

2) Dont burn ur iso's faster than 4x.

Note: They aren't stupid questions, unless you have been in the computer field doing programming for 20 years.

---

### Post by Obor on 2006-04-04
Go to bios (when booting up, before windows starts, press del / f10 or something pp the on the top of keyboard, can't remember which one)

and chage your boot up sequence so your cd rom is first.

---

### Post by ububaba on 2006-04-04
[QUOTE=Obor]Go to bios (when booting up, before windows starts, press del / f10 or something pp the on the top of keyboard, can't remember which one)

and chage your boot up sequence so your cd rom is first.[/QUOTE]

Hi,

Can I ask a sillier question? Where is BIOS located? How can I get to it?

---

### Post by finwhiz on 2006-04-04
Thanks all. I am now happily posting from Ubuntu.

---

### Post by Bender the Robot on 2006-04-04
When you write, "I burnt the ISO in a CD", do you mean that you used the .ISO  to create a bootable CD or did you just, as many people do, in error, copy the .ISO to the CD?

---

### Post by meborc on 2006-04-04
[QUOTE=ububaba]Hi,

Can I ask a sillier question? Where is BIOS located? How can I get to it?[/QUOTE]
that is a good question ;) ... i would suggest [http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)

you can usually access BIOS by clicking DEL, F2, F8, F10 or other key (it depends on your box) during the bootup time (the first ~10 sec after giving power to computer)

---

### Post by taurus on 2006-04-04
[QUOTE=ububaba]Hi,

Can I ask a sillier question? Where is BIOS located? How can I get to it?[/QUOTE]
With Dell, when you first turn your machine on, there is a message in the upper right hand corner telling what key to press if you want to get into Setup--BIOS.  BIOS is located on your motherboard...  So, you need to change the order of boot if you want to boot from the CD first.  I believe you have it boot from harddrive, CD, floppy (if you have one), and others (like USB or even network).

---

### Post by Bender the Robot on 2006-04-04
Sorry, I cross-posted.

---

### Post by hashimoto on 2006-04-04
[QUOTE=ububaba]Hi,

Can I ask a sillier question? Where is BIOS located? How can I get to it?[/QUOTE]
You can ;-)

Bios is a program that first starts when you boot up you PC. It is located in a memorychip on your motherboard (not on any disc). To get to bios:
- (re)boot your PC
- When the first text appears on the screen it normally tells you to push DEL or ESC or some other keyboard button. Push that button and you will get to bios.
- You need to be quick enough. If you don't succeed first time, you need to reboot again.

In bios you can change the boot order. This tells in which order the PC tries to find an operating system on different discs. Set it to look from CDrom first.

---

### Post by ububaba on 2006-04-04
[QUOTE=hashimoto]You can ;-)

Bios is a program that first starts when you boot up you PC. It is located in a memorychip on your motherboard (not on any disc). To get to bios:
- (re)boot your PC
- When the first text appears on the screen it normally tells you to push DEL or ESC or some other keyboard button. Push that button and you will get to bios.
- You need to be quick enough. If you don't succeed first time, you need to reboot again.

In bios you can change the boot order. This tells in which order the PC tries to find an operating system on different discs. Set it to look from CDrom first.[/QUOTE]
Thanks a lot everyone. I presumed that Linux being another planet, 
one would have to employ some other approach.

---

### Post by YuHoo on 2006-04-04
I have no clue how to do this on laptops, but if you poke around your bios and by some unfortuate reason you turn your computer into a heap of silicon with a blank screen, you can open up the computer and reset it. All computers are different, but they all have 1 jumper that will "clear the CMOS" and it will reset it to the defaults. This is always a good thing to know where it is if you decide to overclock or mess around, or installing radically new components. It's a tad off topic, but it's just something that everyone who dives deeper into computers should look into lest they find the pool they jumped into was drained earlier.

---

