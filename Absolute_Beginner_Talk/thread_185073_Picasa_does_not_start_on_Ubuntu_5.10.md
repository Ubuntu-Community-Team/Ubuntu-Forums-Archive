---
title: "Picasa does not start on Ubuntu 5.10"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by zugu on 2006-05-31
I have Ubuntu 5.10, and I tried to install Picasa for Linux.
However, Picasa does not start. The dpkg installation went smooth, but
clicking the Picasa icon in the GNOME applications menu has no result.
I tried running it from the command line, but I just get 5 seconds of
nothing, and then I'm silently returned to the shell. And there is no Picasa. 

I have also tried "ps aux | grep picasa", but with no result.
I tried restarting GNOME, and then the whole system. I started Picasa
again. I was able to see and accept the license agreement, but that was
all. The main program did not start.

Any help is welcome.

---

### Post by Perfect Storm on 2006-05-31
Try check [http://code.google.com/wine.html](http://code.google.com/wine.html) and see if there's a solution or if the bug is reported.

---

### Post by coolclassic on 2006-05-31
I had the same problem and I found that you need direct rendering activated on your graphics card. They way I solved it was reinstalling the software for your card.

try this command and if the answer is no that is your problem.

glxinfo | grep direct

---

### Post by zugu on 2006-05-31
Thanks for the info.

---

### Post by centyx on 2006-09-09
Is anyone else having this problem? I have direct rendering enabled. glxinfo sais 'direct rendering: Yes.' The funny this is, picasa started the first time I ran it, but after the first run, it won't start.

---

### Post by jordanmthomas on 2006-09-09
Have you tried running it from a terminal?  It might give you some insight as to why it is crashing.

---

### Post by zugu on 2006-09-09
This is now an old problem for me. I had to install the nVidia legacy drivers for my video card in order to have Picasa working without problems. Hope this helps.

---

