---
title: "2 Problems (Trash, and Ubuntu)"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by ProgenitorVirus on 2008-03-08
Okay, I have two problems.

1) There are 2 folders containing drivers for a Samsung printer in my trash I can't delete for some reason;
2) Unexpectedly, with no warning whatsoever, Ubuntu just crashes.  I have no idea why it crashes, but the screen locks and I have to turn the PC on and off.  Any idea why...?

---

### Post by glennric on 2008-03-08
What do you mean that you can't delete them?  How are you trying to delete them and what does the system tell you in response to your attempt to delete them?  

As to your system crash, have you tried Ctrl-Alt-Backspace at those times to zap the x-server?  

For both of your questions more information is needed to help you.

---

### Post by ProgenitorVirus on 2008-03-08
I'm opening the trash, via the icon, and choosing "Empty Trash".

It returns me an error saying:

"X cannot be deleted because you do not have permissions to modify its parent folder."
 X being a bunch of .ppd files gathered when installing a printer.

And for the crashing, no, I haven;t tried that, but I've disabled the driver for my nVidia GeForce 5500 FX card.  I wanna see if it'll change anything.

---

### Post by ProgenitorVirus on 2008-03-08
Disabled the nVidia "Restricted Driver" and it seems to be working without crashing now, but I do want to be able to use this gfx card to its full extent.  Does anybody know what I should download to get my nVidia GeForce 5500 FX Graphics Card working?

And how am I supposed to empty my trash?

Thanks!

---

### Post by halitech on 2008-03-08
sounds like you don't "own" the files in the trash, thats why you can't delete them. try open Nautilus with 

```
gksu nautilus
``` 

then going to your home directory, view hidden folders and delete them by highlighting them, then hold the shift key and pressing the delete button on your keyboard.

---

### Post by glennric on 2008-03-08
To empty the trash type
```
sudo rm -r ~/.Trash/*
```

---

### Post by glennric on 2008-03-08
> **ProgenitorVirus said:**
> Disabled the nVidia "Restricted Driver" and it seems to be working without crashing now, but I do want to be able to use this gfx card to its full extent.  Does anybody know what I should download to get my nVidia GeForce 5500 FX Graphics Card working?

And how am I supposed to empty my trash?

Thanks!

Were you running compiz (Desktop Effects) when you were having the problems?  The default restricted drivers should work fine with that card.

---

### Post by ProgenitorVirus on 2008-03-08
Okay, I thought I had it solved, but it wouldn't seem so.  I tried to start Pidgin IM, and it did the same thing, with the Ctrl+Alt+Backspace thing doing nothing.  I did a memtest, and no errors.  The Visual Effects were also set to off; if there is a pattern to these random crashes at all, its the fact that almost all of them have happened whilst using any program/utility

---

### Post by glennric on 2008-03-08
You may have to seach through system logs to see if there are any errors being reported.  They are all in /var/log/.  In particular check syslog, dmesg, and Xorg.0.log.  That is all I can really say without more information.

---

### Post by ProgenitorVirus on 2008-03-08
Well, I really appreciate your patience and help!  But to give you information, I'd need to know, what you needed to know.  Any specifics?  I'm just starting out on Linux afterall.

---

