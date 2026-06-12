---
title: "GRUB+cordlesskeybar=disaster"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by Mr.Carramba on 2007-12-25
Hello!
And merry Christmas to you all!

My Christmas started well when I received new Logitech Cordless Wave keyboard and mouse, but now it's gone to disaster :(

I can't navigate in the GRUB with it, so I'm "stuck" with default OS, and now when I have entered windows I can't get into ubuntu unless I fire up cd and modify menu.lst .

do you have any suggestions on how to fix this?

thank you in advance!

---

### Post by lswest on 2007-12-25
is the adapter for the keyboard USB or PS/2 (the "old-fashioned" plug for keyboards & mice)?  if it's USB make sure that your BIOS enables USB power before OS boot (at least, that's what it is called in my BIOS) and otherwise make sure that at the GRUB menu screen that the keyboard is "connected" to the adapter. Problem is that the keyboards usually don't send traffic to the adapter during boot up so that they are seen as inactive and that USB port is then not enabled, which can lead to those problems.  That's why i prefer cabled keyboards:P

---

### Post by slimdog360 on 2007-12-25
try connecting your old keyboard and going into your bios. There is a setting in there for usb keyboards. Try enabling that then giving it another go, even with the wireless.

---

### Post by Mr.Carramba on 2007-12-25
Thank you both for quick and correct solution! 
    Strange thing was that keyboard responded fine for entering the BIOS ...

Have one more question regarding Logitech Cordless Wave, where can I change the keyboard/mouse set up so that i can enjoy all those necessary* buttons on mouse and keyboard?

---

### Post by lswest on 2007-12-30
in windows you should be able to do it using a driver that came with it on a CD, or downloaded off the site.  in Ubuntu you can just make certain buttons the keyboard shortcuts for what you need em to do, at least, only way i can think of doing it.  (e.g. for a home shortcut key make it open nautilus)  maybe someone has a better idea?

---

