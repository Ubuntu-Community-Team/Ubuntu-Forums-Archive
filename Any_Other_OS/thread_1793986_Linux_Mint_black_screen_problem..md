---
title: "Linux Mint black screen problem."
date: 2011-06-30
forum: Any Other OS
---

### Post by abnordude on 2011-06-30
I've been using ubuntu for quite a long time.

I want to try out linux mint.
I downloaded the linux mint image from the website and burned it to a disk.

But when I inserted the disk, there were two lines at first [which read something about "isolinux" or something]. And then the screen went black.
i then burned at the lowest speed and still I get the same problem.
This was my experience with linux mint 10 CD.

_____________________________________________________________________________________

I downloaded the linux mint 11 DVD and burned [at the lowest speed].
But when I inserted the DVD, I get the same problem.

_____________________________________________________________________________________


I went to my friends computer. I put the linux mint 10 CD in his PC.
And......
There it was. 
It was working well.

My friend has a windows xp [ Dunno if this helps, but still ]

---

### Post by NightwishFan on 2011-06-30
Right when the CD menu loads and you would press enter to boot mint; You can probably press a key (tab?) to edit the boot options. Add a space at the end and type:
```
nomodeset
```

Then press enter to boot. Does it work?

---

### Post by abnordude on 2011-06-30
I think I got it.

I changed the BIOS settings.

from IDE to AHCI.

It worked.

Thanks for answering.

---

