---
title: "Gimp + Mouse + Tablet"
date: 2008-02-20
forum: Art &amp; Design
---

### Post by SpiderGorilla on 2008-02-20
Having a very weird problem with my Gimp and my Mouse. I've got a Wacom Bamboo attached to the computer, and I can manipulate everything absolutely fine with the tablet. Absolutely no problem. But the mouse... I can only use it for the menus and buttons. Any time I try to use it to do anything to the actual drawing, such as selections, drawing, erasing, anything like that... it doesn't accept the input from the mouse.

Any idea what's up? I'm using 7.10 and Gimp 2.24...

---

### Post by Curtisc on 2008-02-20
I've had the same issue since Breezy, both with a Graphire2 and a Bamboo.  I gave up trying to fix it, although I used to have the same issue with Inkscape and now I don't, so it must be a fixable problem.

I just checked now, and my mouse shows up in the "extended input devices" screen, but if I try to use it gimp freezes (turns grey) and I can't use my computer at all until it unfreezes.  Is your mouse listed as an extended input device?

---

### Post by SpiderGorilla on 2008-02-20
Nope. I checked that. I wonder if it's because I don't have the "pad" option for my Wacom in xorg.conf that causes it. My tablet doesn't come with a mouse, but you never know.

---

### Post by SpiderGorilla on 2008-02-25
Sorry to pull this one out of the gutter, but the problem has extended itself.

Now it's randomly losing tablet, execpt at the highest possible pressure. It'll restore after a restart of the application, but this will literally happen from one stroke to the next. Nothing special will happen, but sometimes it occurs when I switch between eraser and back to the brush tool.

This is really annoying as I do all original compisitions in GIMP right now, and I really don't want to try to download and install ArtRage through Wine again.

Anyone have any clues?

---

### Post by kiddo on 2008-03-07
I'm having the "mouse is blocked by the presence of the tablet" problem in the gimp, had it for as long as I can remember, but it does not affect inkscape. Both are configured the same regarding input devices.

[SIZE="6"]Oh... wait. No they are not![/SIZE]
I just **fixed it** while writing this! There are 3 modes for each input device. For the regular mouse to work alongside the tablet, it **MUST be disabled** in the extended input devices!

I made a small video to show you: 
[http://tuto.ecchi.ca/wacom%20et%20souris%20qui%20coexistent%20dans%20gimp%20et%20inkscape.ogg](http://tuto.ecchi.ca/wacom%20et%20souris%20qui%20coexistent%20dans%20gimp%20et%20inkscape.ogg)

---

### Post by Curtisc on 2008-03-13
> **kiddo said:**
>  For the regular mouse to work alongside the tablet, it **MUST be disabled** in the extended input devices!

Wow... that fixed it for me too.  After all these years, I never though disabling the mouse would be the right solution.

Spider, have you gotten your mouse to show up as an extended device?  Mine never did until I got a fancy new mouse (Logitech bluetooth MX1000) that required some extra configuration.  It's using the evdev driver.  The "Configured Mouse" default device doesn't show up in the extended devices, so maybe it's a driver thing?  Although in kiddo's video it looked like his is "Configured Mouse", so maybe that's not the trick...

---

### Post by qubodup on 2008-06-22
> **kiddo said:**
> 
[SIZE="6"]Oh... wait. No they are not![/SIZE]
I just **fixed it** while writing this! There are 3 modes for each input device. For the regular mouse to work alongside the tablet, it **MUST be disabled** in the extended input devices!

I made a small video to show you: 
[http://tuto.ecchi.ca/wacom%20et%20souris%20qui%20coexistent%20dans%20gimp%20et%20inkscape.ogg](http://tuto.ecchi.ca/wacom%20et%20souris%20qui%20coexistent%20dans%20gimp%20et%20inkscape.ogg)

It helped me too (with a bamboo). Best of thanks kiddo!

---

### Post by henriet on 2008-07-19
Hello,
I've just bought a Thinline Tablet and I face the same problem : I can't use the mouse in the image's windows in gimp, even when the mouse is disabled in "Extended Devices". Does anyone have an idea to solve this problem ? Thanks.

---

### Post by Xfcn on 2008-07-19
Still not working for me. Mouse is disabled, and I'm still not able to use my mouuse in Gimp. Which is really effing annoying as I do a lot of pixel-based work and it doesn't function right with the tablet (about 40x's more effort than it ever needs to be).

Of course, I just found JDraw through a different search and it... it does exactly what I need for it to do! Yes!

---

### Post by dgrafix on 2008-07-21
I tried to download that jdraw and got a .jar file. Ive no idea what to do with it. I got java from synaptic but cant seem to run it (it opens in package manager tho). Sorry im not a java programmer but would like to check it out :)

---

### Post by Xfcn on 2008-07-21
Do the following:

Applications > Accessories > Terminal

$> java -jar JDraw.jar

Please replace JDraw.jar with whatever the file name is you downloaded.

If you want to make it a menu-bar launchable item, do the following:

System > Preferences > Main Menu > Graphics > New Item...

Type: Application
Name: JDraw
Command: java -jar /path/to/JDraw.jar
Comment: Java-based pixel art application

And Bob's yer uncle, matey.

---

### Post by Xfcn on 2008-07-23
Aha! Figured it out (for me). I'm using the Wacom Bamboo as described here. Here's what I did:

1) Set Mouse to Disabled
2) Set Eraser to Disabled
3) Set Pad to Disabled
4) Set Cursor to Disabled
5) Set Stylus to SCREEN

Using GIMP 2.4.5 whatever is default with Ubuntu 8.04 as of April 3rd or so.

---

### Post by lbharti on 2009-09-16
Disabling any of cursor, or eraser would take away Gimp's sensitivity to them, i.e. the selected tool would not change with the tip facing the tablet. I am using Wacom Graphire 3 and have the same problem. I do not have a solution yet.

---

