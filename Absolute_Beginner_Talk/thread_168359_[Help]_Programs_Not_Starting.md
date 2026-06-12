---
title: "[Help] Programs Not Starting"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by bugme on 2006-04-30
Hello,
I have just installed Ubuntu, but when I click on a program, like GIMP, it said starting GIMP in the toolbar for a ~5 seconds, then that disappears and nothing happens.
Thank you in advance!

---

### Post by gingermark on 2006-04-30
Try running it from the Terminal.

Open Terminal, type "gimp" (and press Enter) and see if it gives you any information as to what might be happening. You can then post such information here, so that others can help you better.

---

### Post by bugme on 2006-04-30
When I click Applications>Accessories>Terminal is sais 'starting terminal' but the same thing happens (it never starts up).

---

### Post by catlett on 2006-04-30
Try starting in "recovery mode". When you start the computer the boot manager gives you options. Choose Ubuntu (recovery mode).
First off if you get into recovery mode and nothing works, your install is no good. This could be for a variety of reasons. If I had to pick I'd say the cd image has a problem. Did you download and burn it or did you order it through "ship it"?
If you get in the recovery mode get to the terminal ,or if you just get the command line log in, type ```
sudo dpkg-reconfigure xserver-xorg
```
This will take you through the x server configuration. Try to put in as much info as possible about your hardware. If you have a working computer go online to the maker of your computer's website. They will usually have specificatuions available.
If nothing works and you downloaded the image. Burn the iso again but this time do it at 4x speed. It will take longer but will ensure a better copy is made. That could be the original issue (cd burned at too high a rate and the image has inconsisitencies). Good luck.

---

### Post by gingermark on 2006-04-30
OK, that is just plain odd.

Which version of Ubuntu are you using (Breezy, Dapper etc, otherwise known as 5.10 or 6.06) ?

You said this is a fresh install. Have you done / changed anything at all? Are you posting this in Ubuntu? If so, obviously your browser works, so aside from the Gimp and Terminal are there any other apps you've tried that don't work? Or indeed, which ones have you tried that do work?

Sorry for the vagueness here, but this seems a very unusual problem for a fresh installation, and so any additional information you can give will hopefully help someone diagnose the problem.

EDIT: Just read catlett's post. Seems sensible, maybe do that first :)

---

### Post by bugme on 2006-04-30
I resolved the problem!
It turns out that when I changed the host name of my system, none of the programs would start. A reboot was all I needed!
I'm sorry if I caused any confusion.

---

### Post by gingermark on 2006-04-30
Well, that's useful for anyone who runs into the same problem. Glad you got it sorted.

---

