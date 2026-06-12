---
title: "feisty &quot;failed to set xfermode&quot; error"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by zabdar on 2007-04-23
I've only seen remedies for this problem if some form of Linux was already installed on the machine. What if I'm moving from Windows to Linux? Does anybody have a workaround for the controller bug if you don't already have Ubuntu on your machine? Or am I screwed and just have to buy a new pc so I can run vista?

apologies if this already posted somewhere- if it is it isn't among the search results for  "failed to set xfermode".

Thanks.

---

### Post by fak3r on 2007-06-26
Feisty still works fine, it just takes more time to boot (+2 minutes for me).  The 'irqpoll' work around is documented many places, I have a HOWTO for it  here: 
[http://fak3r.com/2007/06/22/failed-to-set-xfermode-solved/](http://fak3r.com/2007/06/22/failed-to-set-xfermode-solved/)
My concern is why does this keep cropping up with each kernel upgrade?  Obviously it's a bigger problem if it's recurring like this on so many instances.

---

### Post by PacShady on 2007-07-01
> **fak3r said:**
> Feisty still works fine, it just takes more time to boot (+2 minutes for me).  The 'irqpoll' work around is documented many places, I have a HOWTO for it  here: 
[http://fak3r.com/2007/06/22/failed-to-set-xfermode-solved/](http://fak3r.com/2007/06/22/failed-to-set-xfermode-solved/)
My concern is why does this keep cropping up with each kernel upgrade?  Obviously it's a bigger problem if it's recurring like this on so many instances.

The reason the problem comes up at every kernel upgrade, is because at each upgrade the grub menu.lst is updated. You can set the 'irqpoll' option in a section of your menu.lst that sets it each time for the default kernel when it's updated:

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
```

Just add your new option to the "# defoptions=quiet splash" line, and each time the kernel updates it will add the option to the end of the line for you!

'Shady

---

### Post by rhempel on 2007-12-19
I've been seeing this error in my dmesg too. I am using an older Asus P4C800 motherboard and a newer Samsung HD300LD ATA drive as the slave drive.

My dmesg was showing the old Seagate 120G drive as the primary and properly configured for UDMA100.

The Samsung drive comes factory configured for UDMA133.

On a whim, I booted an Ultimate Boot CD and ran HDIAG from Samsung for drive diagnostics. I forced the drive to only report UDMA 100 (which is the highest supported by my BIOS) and voila, the drive is now recognized!

I only hope that the BIOS also allows for a 300G drive....time to go check

Ralph

---

