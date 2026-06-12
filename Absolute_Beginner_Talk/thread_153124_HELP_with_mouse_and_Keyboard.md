---
title: "HELP with mouse and Keyboard"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by jolger on 2006-03-31
I've got a Canyon wired Laser mouse and a microsoft wireless keyboard + mouse (not using the mouse there)

now the problem is that after a while (in kde) the mouse stops working and just stands still on the screen... a few seconds/minuttes later the keyboard stops working...

anyone got some advice on what to do???

p.s. both mouse and keyboard run on usb...

---

### Post by jolger on 2006-03-31
could someone PLEASE help me with this??? its really frustrating to have to "force" a restart all the time :(

---

### Post by Mustard on 2006-03-31
[QUOTE=jolger]could someone PLEASE help me with this??? its really frustrating to have to "force" a restart all the time :([/QUOTE]

I'd help if I knew what the answer was. :)  Some problems are so obscure that only a few people know the answers.  Keep trying.

---

### Post by jason.b.c on 2006-03-31
[QUOTE=jolger]I've got a Canyon wired Laser mouse and a microsoft wireless keyboard + mouse (not using the mouse there)

now the problem is that after a while (in kde) the mouse stops working and just stands still on the screen... a few seconds/minuttes later the keyboard stops working...

anyone got some advice on what to do???

p.s. both mouse and keyboard run on usb...[/QUOTE]

Why aren't you using the wireless mouse.? :confused:  There really cool.!:) 

I don't think the problem is with your mouse.!  Some kind of configuration problem.

---

### Post by jolger on 2006-03-31
well actually i did try using the wireless mouse but it was still the same problem...

---

### Post by jason.b.c on 2006-03-31
[QUOTE=jolger]well actually i did try using the wireless mouse but it was still the same problem...[/QUOTE]

Can you not hook up that mouse and keyboard to the **PS/2** ports of your computer???:confused:   Instead of **USB** *a.k.a* universal serial bus..:)

---

### Post by stinkykid on 2006-04-23
I was having the same problem over the last few days... my keyboard and mouse both fairly inconsistently stopped working at variable time lengths.  Sometimes a few minutes, sometimes immediately...

*The solution was a bit messy and done in a panic.  I wasn't sure of the exact cause of the problem, though this method did solve it.  The one thing I do know is that this is a driver issue through and through.*

***Here's what I did:***

[LIST=1]
[*] ***I recompiled my kernel.***
I compiled the following into the kernel rather than using modules as per the default Ubuntu setup:
[LIST]usbhid (USB Human Interface Device (full HID) support)[/LIST]
[LIST]usbcore (Support for Host-side USB)[/LIST]
[LIST]ehci-hcd (EHCI HCD (USB 2.0) Support)[/LIST]
[LIST]uhci-hcd (UHCI HCD support)[/LIST]
Now... not all of these are necessary I don't believe, but I used all of them and it can't hurt since they'll just be loaded as modules anyhow.  I thought that this would solve both of my problems, but it only fixed my keyboard... which was the more important one.

[*]***I replaced the mouse.***
I couldn't figure out why the mouse was still not working.  I tried different approaches for hours to try to remedy the problem, to no avail.  I eventually got another, more recent USB mouse, which remedied the problem immediately.  I am not too sure of the reason why it was fixed at this point.  One thing I did notice is that when I issued 'dmesg' to examine the kernel logs the old mouse (cheap-o $10 Logitech roller-ball style) listed as being a 'usb' mouse, where as the new mouse ($15 Logitech optical) was listed as being 'usbps'.  I am not sure of the meaning of 'usbps' though, it does seem to be readily compatible with more systems than the older one.  It may be a more robust protocol or something.
I wish I could give you a better solution than that for your mouse.  It sounds like you've got a couple that aren't working.
[/LIST]

**Here are a few more suggestions if applicable:**
[LIST]In your BIOS enable support for legacy USB devices.[/LIST]
[LIST]In your BIOS have the mouse and keyboard be setup/controlled by OS instead of by the BIOS[/LIST]
[LIST]In your BIOS enable interupts for USB devices[/LIST]

Just remember... this is most likely a driver issue.  The solution will most likely lie in one of three realms:
[LIST]Make your computer more compatible with Linux/Ubuntu by configuring your BIOS[/LIST]
[LIST]Make your operating system more compatible with your BIOS by configuring the kernel[/LIST]
[LIST]Get different hardware![/LIST]

I hope this helps

---

