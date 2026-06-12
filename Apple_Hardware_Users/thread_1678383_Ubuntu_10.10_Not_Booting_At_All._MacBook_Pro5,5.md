---
title: "Ubuntu 10.10 Not Booting At All. MacBook Pro5,5"
date: 2011-01-30
forum: Apple Hardware Users
---

### Post by rtyb on 2011-01-30
Okay, so i just recently installed Ubuntu 10.10. Did the usual stuff, updates, configure, add ppa:mactel repositories, etc...

But after finishing installing updates, i rebooted, and it would hang, like if it wasn't recognizing the display. It would hangup just after the ubuntu and "....". Loading screen. I've tried everything i could. Cuz to startoff, there's no way i can boot in recovery mode. I've done each and every single thing, from nividia-current, to restart x, i try but no xfix available, seems like the comand line i'm barely managing to boot in, isn't completely functional.

Recovery mode fails. Stucks at this screen where it's doing stuff like"ide 3 usb super high speed, ".  Etc...

Boot with CD but...doesn't even boot it, just sends me to grub, where i choose c command line, i can't do anything. Try kernel 2.6.22 and 2.6.25. BOth normal and recovery mode. Already did memtest, tried packages (installing nvidia crap). Nothing at all works. A single update broke Ubuntu. How the....

BTW! Yes, already blessed with osx...

---

### Post by rafamundez on 2011-01-30
This happened to me too...I have the exact same version of your Macbook Pro.  I had to format the entire thing and start out fresh.  I couldn't find a solution and I had everything backed up so I just did a clean install of Snow Leopard.

I was using the 64 bit version of Ubuntu, were you using the that as well?

---

### Post by rtyb on 2011-01-30
No, i was (or am) using 32-Bit. Don't even think of 64 Bits. It's just trouble you're getting into. Stick with 32 Bit. Same stuff. More support. Easier..

So i didn't find a solution, but i think the problem was i destroyed the EFI partition in the first install. I did it on purpose, EFI to me seems useless, but well.
In the end, i used the OSX Install CD and with Disk Utilities, wiped fresh my 250Gb Hitachi HDD.
This time i kept the 209Mb EFI Partition. So far, haven't had any trouble yet.

---

