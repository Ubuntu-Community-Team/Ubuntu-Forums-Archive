---
title: "[SOLVED] Increasing the sizeof the partition Ubuntu is on"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by MangasColoradas on 2007-12-16
I am downloading gparted live cd now, this is my setup--

sata1 20gb with windows on and the rest is ntfs

sata2 60gb with Ubuntu on it and the rest is ntfs

I just want to make the whole of sata2 Ubuntu, so am I increasing the ubuntu partition/s and if so which, as there are swap partitions etc. which I am not used to--or can I reduce the ntfs partition on sata2?

Sorry if these are dumb questions...:)

---

### Post by MangasColoradas on 2007-12-16
I just tried gparted out and my monitor says 'out of range'? 

I think I can get around it by enabling vesa drivers at the start?

Or, would the alternate install Gutsy disk work just as well?



Edit

Cant get gparted working, no option to change to vesa drivers. Should I enable vesa drivers before logging out of Ubuntu?

---

### Post by mikewhatever on 2007-12-16
Gparted is a better tool, because of its graphical environment. It is more intuitive and a lot easier to use compared to the alternate CD.
Frankly, I do not quite understand the need to redo your partitions. 60 GB should be more then enough for Ubuntu's /. Think of the benefits of expanding it. Are they worth the trouble? Why not use that other partition for storage or backup? Messing with partitions may render your system unbootable.
If you still want to, then, delete the unwanted partitions and expend root into unallocated space. You may want to read Gparted documentation before that.
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)  Hope everything goes fine.

---

### Post by MangasColoradas on 2007-12-16
Thanks Mike, can I download and save stuff the rest of the sata 2, the ntfs part?

That part has to me mounted doesnt it?

---

### Post by logos34 on 2007-12-16
> **MangasColoradas said:**
> I think I can get around it by enabling vesa drivers at the start?

that's what I have to do...I mostly use Parted Magic now, but even there I have to use the 'Xvesa' driver

I'm not sure if you can resize partitions by going into 'rescue a broken system' on the alternate cd...you can mount them and poke around but i'm not sure about the rest (that's something I should know, and although I install a lot using the text-mode alt cd I hardly ever use it otherwise, I have the ubuntu live cd with gparted on it for that).

---

### Post by MangasColoradas on 2007-12-16
> **MangasColoradas said:**
> Thanks Mike, can I download and save stuff the rest of the sata 2, the ntfs part?

That part has to me mounted doesnt it?

I can! LOL

I just checked...thats great!

Thanks Mike!

:)

---

### Post by MangasColoradas on 2007-12-16
How do I say this is solved?

[SOLVED]   ???

---

### Post by mikewhatever on 2007-12-17
Click on Edit and then Go Advanced. There is a good how-to for permanently mounting NTFS, in case you ever need it in the future.
[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

Cheers!

---

### Post by MangasColoradas on 2007-12-17
Thanks again Mike. :)

---

### Post by MangasColoradas on 2007-12-17
Well, I have edited the first post title to say [solved] but it isnt showing...

---

### Post by kpkeerthi on 2007-12-17
Here is how you mark the thread as SOLVED

---

