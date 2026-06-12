---
title: "Install problems"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by ShadeOfGreen on 2006-04-03
I am brand new to Linux and I burned an image of Ubuntu 5.10 and planned to put it onto a brand new hard drive (Maxtor120G).  

First I tried to install but I burned the image too fasst and it wouldn't work (Parts of the install just didn't work).

So I made a new burn installed, things went great.  I rebooted did all I needed to do and than like magic I had Ubuntu.......for about five minutes.  Just as I was exploring the interface and getting a feel, my screen went suddenly blank and began to reboot, only when it booted I got a page full of code with this at the bottom.

Kernel Panic - nont syncing: Attempted to kill idle task.  

Now this happens everytime, or code flys by on the screen I can't read it and it just goes on and on.  I got to the Ubuntu splash once but it failed to start and launched a reboot.

Help please?

---

### Post by r4ik on 2006-04-03
I am affraid your BIOS does not support the size of the disk.
May i ask what size the old one was ?

---

### Post by ShadeOfGreen on 2006-04-03
I had two before.  A sixty G Master with a forty G slave.  The motherboard is an Asus A7N8X Deluxe.  

I also just ran memtest only to find that once it approaches 65% the test reports and endless string of failures.

---

### Post by r4ik on 2006-04-03
[QUOTE=ShadeOfGreen]I had two before.  A sixty G Master with a forty G slave.  The motherboard is an Asus A7N8X Deluxe.  

I also just ran memtest only to find that once it approaches 65% the test reports and endless string of failures.[/QUOTE]

The disk is oversized and not supported imo sorry.
Replace the old one's and reinstall you should be fine.

From the Mailing List,

"In my experience, kernel panic is hardware based. But the only times I've
ever seen it were while I was using an oversized hard drive in a machine
that had an old BIOS limit on hdd capacity."

Hope it helps.

Good luck.!

---

### Post by catlett on 2006-04-03
Check with the maker of the motherboard and see if there is an update for your bios. If there is you might be able to use your large size drive after the bios update. I tried to search Asus but I kept getting redirected to an error page. If their site is up, that's where you'll find the info about an update and directions to flash your bios update.

---

### Post by r4ik on 2006-04-03
[QUOTE=catlett]Check with the maker of the motherboard and see if there is an update for your bios. If there is you might be able to use your large size drive after the bios update. I tried to search Asus but I kept getting redirected to an error page. If their site is up, that's where you'll find the info about an update and directions to flash your bios update.[/QUOTE]

The site is up,

[http://support.asus.com/download/download.aspx?SLanguage=en-us](http://support.asus.com/download/download.aspx?SLanguage=en-us)

I could not find anything about a Asus A7N8X Deluxe board and i would not recommend bios flashing unless he is sure what he is doing.
Just my opinion :)

---

### Post by ShadeOfGreen on 2006-04-03
I got it up and running.  No BIOS flashing required.  I removed a stick of RAM that was apparently failing and the very next time I booted up it worked.  

Thanks a lot guys.  The reputation of Linux users being helpful seems to be on the money.

---

