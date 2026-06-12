---
title: "Duel boot OSs?"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Outlawfencer on 2007-06-20
I've been running ubuntu feisty 64-bit for a few weeks now. I have tried to get some of my windows games to run on it, but it doesn't look like it's gunna happen. I I have decided to re-install windows on my machine, just to play games(ugh!). and I'm trying to figure out how to make it so I can choose which OS I want to boot in.  I'm still pretty new to all this Linux stuff, so any help, or a link to a guide would be nice. 

Currently have installed:
250 gig HDD with Dapper 64-bit installed(I can lose this if need be)
250 gig HDD with Feisty 64-bit installed(I don't want to lose this, but I can if i have to)
AMD Athelon x64 Duel core CPU
Nvidia 7900 GTX 512mb Video card
4 gigs DDR ram installed, 3 gigs usable

Not sure If I'll have to delete everything just to get windows on( MS jerks! )but I have all my important data stored on an external HDD, so if I have to wipe everything, I can.

Well thanks for your time
~Outlawfencer~

---

### Post by GrueTamer on 2007-06-20
Ubuntu has only automatically chosen which OS to boot when GRUB is installed and it doesn't find any other OS's, so if you put windows on there, you'll have to add windows to the boot entry, and stop grub from automatically choosing ubuntu.  I can help you do this, but I need to see you /boot/grub/menu.lst file.

It may be easier to install windows, and then install ubuntu again afterwords, to eliminate other possible problems that you may have.  And with all the data on the external HDD, this may be the best option.

---

### Post by Outlawfencer on 2007-06-20
thanks, I didn't wan to have to wipe it, but I guess windows is juts a jerk.

---

