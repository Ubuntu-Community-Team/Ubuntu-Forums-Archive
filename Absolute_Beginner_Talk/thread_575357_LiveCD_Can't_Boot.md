---
title: "LiveCD Can't Boot"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by Cheese Roller on 2007-10-13
Here's the problem.

The Computer wont turn off!

This is a hand me down I just got. (Not my primary computer thank god.)

Whenever you click shut down the system restarts. There's no way for me to change boot order.

Is there an alternative method for changing boot order?

(Windows XP, unsure of service pack but I  think it's 2)

UPDATE: Okay I fixed it, I pressed F8, now what  do I  do?

---

### Post by Cheese Roller on 2007-10-14
bump

---

### Post by slughappy1 on 2007-10-14
Will it still not boot? Or do you get an error while running the cd?

---

### Post by Cheese Roller on 2007-10-14
The Kubuntu installer wont come up, it just autoloads the OS.

I'm asking how to change the boot order.

---

### Post by slughappy1 on 2007-10-14
I'm not sure about your computer, but on my desktop I had to edit the bios before I could load from a cd, not that hard. It is pretty straight forward. And on my laptop I just press F12 and tell it the cd rom. Hope that helps some

---

### Post by Cheese Roller on 2007-10-14
Sorry, that didn't help.

F12 did nothing.

Is there any way  to change boot order without  doing it on the restart?

---

### Post by Cheese Roller on 2007-10-14
bump again...

---

### Post by Cheese Roller on 2007-10-14
bump yet again.

Wow these forums have been really bad at answering my questions lately.

---

### Post by mikeserv on 2007-10-14
During the boot sequence at the very beginning there should be some kind of splash screen that displays a little bit of BIOS info - maybe motherboard type, as well.  Somewhere on that screen you should see something like "Press [key] for options."  Usually that key is delete or or Escape - but it's definitely something.  You have to press it during the first couple of seconds during boot-up, though.  When you do get into the BIOS, be wary!  You can really mess some stuff up in there.  But what you're looking for is something that has to do with boot order.  Just add your CD drive, or, and this is more likely, if it's already there move it to the top of the list - above the harddrive.  

-Mike

---

### Post by Cheese Roller on 2007-10-14
There's nothing like that.

First thing it shows is the loading XP screen.

---

### Post by klapauciuspdx on 2007-10-14
Near as I can tell, you've using a Mac as your primary.  Unfortunately, the functionality that you're looking for, I would guess, would be to press 'c' to boot off the CD.  This doesn't generally work on standard PC's ( some will support, some not, but generically, it's not something that's normally supported.  In general, you have to change the boot order in the BIOS. Macs use EFI, which is somewhat different, and frankly, a heck of a lot better.

Generally, depending upon the machine, during the POST (self-test), you'll see something like 'Press DEL to enter Setup' or something along those lines.  I've seen F2 used, F10 ( this is generally Compaq, and you'll have to do it before the little blinking line cursor disappears, it's a pain in the backside ), F12, and Del.  Much older ones used something like Ctrl+<some key>, but they're not likely to run XP.  Once you're in, there'll be a number of options, some will specifically say 'Boot' as a submenu, others, you'll just have to look in the various submenus until you find something that resembles a boot order menu.  You should at that point, be able to select the CD as the first thing to boot from.  When I have set up my own machines, I've usually set them to boot from CD and then the hard drive, I haven't got a floppy for any of my machines, unless you count the USB floppy sitting in a box just in case I need it.  

Once you've set that, you should be able to save the changes, the machine will reboot, and you should be able to boot off your CD.  If you have any questions, feel free to leave me a message.

K.

---

### Post by 001100 on 2007-10-14
on ur mobo theres jumpers do a reset of the bios and boot from cd. reburn the cd again just to make sure burn at 4x and if that doesn't work try hooking upaother cd-rom drive and try again

---

