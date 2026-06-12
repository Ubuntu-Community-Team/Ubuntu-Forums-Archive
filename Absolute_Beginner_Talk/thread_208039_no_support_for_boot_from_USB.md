---
title: "no support for boot from USB"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by rum and monkey on 2006-07-02
I've recently installed ubuntu onto my 160 gb western digital external harddrive and everything went fine during the install, but I ran into one huge problem. How can I possibly boot from the harddrive if I have no "boot from USB" support in my BIOS? My BIOS shows up as Insyde Software Corporation Version 2.06 08/10/04. I talked to my friend's dad about this (he's a programmer) and he suggested getting around this by creating a small partition in my internal harddrive and creating a file in it that would somehow tell the computer to boot from the USB port. My first question is: Is this at all possible? My second question is: How can I go about doing this? I'm not *extremely* into programming, but I know a little bit about it, and I don't know how to make that file. My final question is: Is there any other way (or any way at all) around no BIOS support for booting from a USB drive?

---

### Post by dickohead on 2006-07-03
Get a motherboard that supports boting from USB... or see if you can enable it in yours.

Or like has been suggested, get a small harddrive, install Grub onto it (unsure on specifics) and point it to your USB drive, check google or linuxquestions.org I'm sure this will have come up before.

---

### Post by rum and monkey on 2006-07-03
I made a small partition on my main internal drive, about 7 mb, and restarted the comp to look in my BIOS to see if I could boot from it. Nope. My boot options never seem to change, no matter what I have plugged into the comp, or what drives I have internally. I looked at the main screen of my BIOS, too, and it doesn't even show my USB drive. These pictures were taken when the USB drive was plugged in.
[[IMG]http://img338.imageshack.us/img338/6824/img27615mf.th.jpg[/IMG]](http://img338.imageshack.us/my.php?image=img27615mf.jpg)
My boot options
[[IMG]http://img443.imageshack.us/img443/6421/img27626em.th.jpg[/IMG]](http://img443.imageshack.us/my.php?image=img27626em.jpg)
My startup menu
[[IMG]http://img443.imageshack.us/img443/8922/img27642tu.th.jpg[/IMG]](http://img443.imageshack.us/my.php?image=img27642tu.jpg)
And my main BIOS menu

---

