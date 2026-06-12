---
title: "[SOLVED] URGENT Theres something on my new PC Fujitsu blocking linux boot CDs"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2007-10-08
Hi

Ive got a brand new Fujitsu seimens pc. I need to get ubtu installed tonight and have a big problem.

Ive tried with both ubuntu and fedora and have the same problem. They fail just after the linux image upacks. The fedora one says cannot find root filesystem, and the ubuntu one gets into some strange shell with the message /bin/sh cant access tty job control switched off..

When i boot into vista, i have 3 partitions on the harddrive, 
EISA components (11Gb) | Windows Vista (75Gb) | Unallocated 65Gb (where i want to install ubunbtu)

I dunno what this EISA components thing is thats nicking up 11gig, could that be why?

I dont get it, i thought the live CDs were supposed to not need a HDD.

---

### Post by mramsey on 2007-10-08
> **dgrafix said:**
> Hi

Ive got a brand new Fujitsu seimens pc. I need to get ubtu installed tonight and have a big problem.

When i boot into vista, i have 3 partitions on the harddrive, 
EISA components (11Gb) | Windows Vista (75Gb) | Unallocated 65Gb (where i want to install ubunbtu)

try searching fujitsu seimens here.  I think there is a post here recently.

---

### Post by skymera on 2007-10-08
yeah, Vista is a bugger, many stories.

as said search the forums :wink:

sorry i cant be much of help

---

### Post by philinux on 2007-10-08
Try the ubuntu live cd but choose safe graphics mode

---

### Post by floke on 2007-10-08
You could try the alternative installer?

---

### Post by dgrafix on 2007-10-09
Thanks i tried that in the end and it seemed to get past the image problem.
Now im getting no X in vesa or ati.
Ive checked the ati website but my card must be too new or something as there is no drivers for it at all on their own website!!! (ati radeon mob. x2300HD)

---

### Post by floke on 2007-10-09
A quick google yields 2 potential solutions - though there may be more...

[http://ubuntuforums.org/archive/index.php/t-532318.html](http://ubuntuforums.org/archive/index.php/t-532318.html)

[http://ubuntuforums.org/showthread.php?t=478238&highlight=x2300](http://ubuntuforums.org/showthread.php?t=478238&highlight=x2300)

---

### Post by gn2 on 2007-10-09
> **dgrafix said:**
>  ubuntu one gets into some strange shell with the message /bin/sh cant access tty job control switched off...

To get round that press F6 and enter ACPI=OFF as an additional boot parameter.
That's what's worked for me in the past when I've had that message .

> **dgrafix said:**
>  
I dunno what this EISA components thing is thats nicking up 11gig.

It's the manufacturer's recovery partition where your installation software is stored.
They do this instead of supplying proper installation CD's.

---

### Post by dgrafix on 2007-10-09
Just a thought, seeing as its nt identifying the card at all, would it be correct to assume it does not know what PCI bus id it is on either? I dont know much about what this number is doing but how do i know if it should be PCI 1:0:0? and if not what should it be on?
> To get round that press F6 and enter ACPI=OFF as an additional boot parameter.
That's what's worked for me in the past when I've had that message .


Thanks ill try that with the livecd again and if it works ill check what it sticks in its xorg.conf :)

[edit]

Tried that acpi=off thing (in caps) and still no joy, it just gors to an (initramfs) prompt and says /bin/sh cant access tty job control switched off...

---

### Post by dgrafix on 2007-10-09
Great, that second guide did the trick!

Now to fix the 3D :/


Im getting :

from glxinfo |grep direct

Xlib: extension "XFree86-DRI" missing on display ":0.0"
Direct rendering: no
OpenGl render string: Mesa GLX indirect

Nearly there ;)

---

### Post by tgalati4 on 2007-10-09
There's a reason Microsoft pays money to put a sticker:  "Built for Windows Vista"

---

### Post by dgrafix on 2007-10-10
Yeah, funilly enough though, vista installed great and straight in
 but using it - different story- ive had nothing but problems since i started.

---

### Post by gn2 on 2007-10-10
Did you try acpi=off (lower case) ?

---

### Post by floke on 2007-10-10
Remember - Google is your friend...

[http://www.google.co.uk/search?source=ig&hl=en&rlz=&q=Xlib%3A+extension+%22XFree86-DRI%22+missing+on+display+%22%3A0.0%22%0D%0ADirect+rendering%3A+no&btnG=Google+Search&meta=](http://www.google.co.uk/search?source=ig&hl=en&rlz=&q=Xlib%3A+extension+%22XFree86-DRI%22+missing+on+display+%22%3A0.0%22%0D%0ADirect+rendering%3A+no&btnG=Google+Search&meta=)

---

### Post by dgrafix on 2007-10-13
I think ive fixed it, well, i didnt, i downloaded the gutzy beta and it seemed to get it all right!

I guess my pc is too new for fiesty :)

---

### Post by floke on 2007-10-14
Glad its all working!=D>

---

