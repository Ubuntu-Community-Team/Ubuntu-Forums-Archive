---
title: "messed update with debian address"
date: 2009-12-09
forum: Apple Hardware Users
---

### Post by neopablo2000 on 2009-12-09
Hi! First, sorry for my english, not my native language. Second, im here because nobody answered my questions on IRC. Third: the problem!
  Im a Gentoo user, but after acquiring a Powerbook G4 i decided to give xubuntu a try. After installing it (some issues about graphic card, but i did solve it), i started investigating it a little. It worked great! And.. some day i wanted to try Tuxcart. I did some research on internet (i couldnt find it on Synaptic) and found a page that talked about adding a debian ftp site. I did, Tuxcart appeared and i did install it. But... then a pop up saying there were new updates came. And what i did? I did update. :D. Bad bad thing... It started to complain about installation problems, and then i realized the mistake. But it was late... After restarting, i cant start session. It starts, goes to the mouse screen, and after a minute or so, it restarts. I started it whith the cdrom, trying to figure out whats wrong. After some research, it looks like there is a problem with dbus, hal and a lib named libc6. Tried reinstalling them, but nothing happens. I then tried to uninstall them, but the system complains about essencial packages being uninstalled too, looking at them they are almost everything, so i abort. I dont know what to do next. Is there any way to roll back the last upgrade? Is there any way to uninstall this packages without uninstalling dependencies? I want to try as many options as i can before going to a full reinstall. Any more data, please, tell me. Thank you very much!

---

### Post by gordintoronto on 2009-12-09
I'm sorry, I can't help you with dbus, hal and libc6.  You might need to back up your data and re-install from scratch.  (You can use the live CD to do the backup.)

Then, using Synaptic, you could install supertuxkart and avoid problems with upgrades.

---

### Post by neopablo on 2009-12-09
ok, thank you very much!!

---

