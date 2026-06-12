---
title: "Help with a laptop"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2008-03-19
I have an old IBM Thinkpad laptop. It was working fine just a few hours ago, and now it won't load live CDs (or anything else, for that matter). I've tried loading the DSL live CD, which this machine did earlier, and now it won't. About 2 hours ago, I replaced one of the RAM modules with a larger one, and that seems to be when things went awry. Could this have had negative...oh, I can't resist it...ramifications? :lolflag:

I really need to get this machine working again, and I just can't figure out why it isn't all of a sudden.

When I turn it on, it goes to the initial POST splash screen, proceeds to load the initial DSL (or Ubuntu or whatever) bootsplash, and when I hit enter to go ahead and boot, it tells me it's loading the kernel, then the screen goes dark, it seems to hang, and it never recovers. Also, after that hang, I've noticed that two of the LEDs flash at me - the CAPS lock one and the one next to it, which is either num lock or scroll lock.

I'm stumped!

---

### Post by Dr Small on 2008-03-19
Do you currently have an OS on it, or not?

---

### Post by spiderbatdad on 2008-03-19
That happened on my old thinkpad initially. Either a difficulty loading harware or bad usplash.conf
I literally waited 10 minutes once, hitting the esc key 4-5 times every few minutes...it finally loaded. Then I edited /etc/usplash.conf to 1024x768 and the problem was solved. This was for Gutsy.
The 2.6.24-12 kernel in Hardy is still having trouble recognizing the hardware. Hardy loads but it takes forever.

BTW you should have a minimum 512 ram for gutsy.
Also the thinkpad bios has a "config" menu. You want to make sure display is set to "analog vga" in there.

---

### Post by doctorbighands on 2008-03-19
There is currently no OS installed to HDD. That's actually what I'm attempting to do! I want DSL on there for purposes of speed and space-saving.

I'll take another peek into the BIOS. I thought I covered it exhaustively, but it doesn't hurt to look again.

---

### Post by handydan918 on 2008-03-19
> Could this have had negative...oh, I can't resist it...ramifications? 

That's terrible. You should be (I can't resist either...)
PUNISHED!

Seriously, I would ensure that the new ram is being recognized in the bios, and if it is, consider running memtest from the grub menu. (This will takes several hours, depending on how much ram is installed.)

---

### Post by doctorbighands on 2008-03-19
Fearing a problem, I replaced the new RAM with the original stuff. It didn't solve anything.

It's the weirdest thing...as soon as DSL starts to tell me it's loading the kernel, I can hear this very soft "click" sound, and it seems almost like the machine goes into some kind of sleep mode. No amount of hand-dragging across the keyboard will bring it back.

Also, I went back over the BIOS with the ol' fine-toothed comb, and found nothing that allowed me to select "analog VGA." The closest is the screen-on-boot setting, which is currently set to LCD (the other options being CRT or BOTH).

---

### Post by jimrz on 2008-03-19
> **spiderbatdad said:**
> That happened on my old thinkpad initially. Either a difficulty loading harware or bad usplash.conf
I literally waited 10 minutes once, hitting the esc key 4-5 times every few minutes...it finally loaded. Then I edited /etc/usplash.conf to 1024x768 and the problem was solved. This was for Gutsy.
The 2.6.24-12 kernel in Hardy is still having trouble recognizing the hardware. Hardy loads but it takes forever.

BTW you should have a minimum 512 ram for gutsy.
Also the thinkpad bios has a "config" menu. You want to make sure display is set to "analog vga" in there.

FYI: have my older 600x (PIII 500) running hardy (standard gnome desktop) quite nicely with 384 Mb ram. Some older models, mine included, develop some issues with some pcmia cards when ram is maxed out to 512, therefore in these cases 384 can actually be the better choice.

---

### Post by doctorbighands on 2008-03-19
It occurs to me that I may also have hot-switched a PS/2 mouse (plugged it in while the system was powered on). Could that somehow be the culprit here?

Yes, I realize I'm grasping at straws here... :)

---

### Post by LeoSolaris on 2008-03-19
I used to have an ancient Thinkpad A30, and when it's motherboard finally kicked the bucket it at least had the decency to put it up on the screen, but I noticed that there were other error messages that come out as blinking lights.

I don't have the website anymore, because I don't have an IBM, but a little bit of google time and you should find it. It's a page from IBM that gives all of their hardware error alerts. Some of them are really strange. I would be willing to bet that something is broken in the system, and that is the meaning behind the blinking lights. It's an old IBM alert.

Leo

---

### Post by jimrz on 2008-03-19
> **doctorbighands said:**
> It occurs to me that I may also have hot-switched a PS/2 mouse (plugged it in while the system was powered on). Could that somehow be the culprit here?

Yes, I realize I'm grasping at straws here... :)

could be, seems mine did not like ps2 mouse back about breezy or dapper or so, although iirc the mouse simply did not work when hot plugged but all else was fine.

try just powering the system off. first try holding down the  power button. if no luck then try removing the battery ([COLOR="Red"]**NOTE**[/COLOR]; if both battery is present and you have it plugged in via power cord you should[COLOR="Red"] **FIRST**[/COLOR] unplug the power cord [COLOR="Red"]**BEFORE**[/COLOR] removing the battery. then remove the ps2 mouse, restore power source and try again without the mouse.

---

### Post by doctorbighands on 2008-03-19
Ok...

I tried reseating the DIMMs...nothing.

I tried swapping the HDD with a different one...nothing.

I've tried every BIOS tweak I can think of, including restoring defaults...nothing

I removed the battery, plugged in the AC power source...and I'll be damned if it didn't boot properly.

So, WHAT GIVES here?!

EDIT: Working with the battery removed leaves a gaping hole in the side of the notebook. There must be something I can do that will allow the machine to function with the battery inserted. It did earlier today...

---

### Post by jepong on 2008-03-20
My ThinkPad is a R30... running Gutsy and upgraded to Hardy Alpha 6.

When I installed Gutsy I used additional boot options... floppy=thinkpad pci=noacpi... to boot the LiveCD.

It works like charm...

---

