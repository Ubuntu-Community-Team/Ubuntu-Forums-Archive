---
title: "Stupid ISO LiveCD Help"
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by Abyssal on 2005-12-06
[SIZE="2"]My peice of crap CD is not working. :mad: 

I try and try, I burned it with ISO Image Level 1 and I tried booting up, went into BIOS and then had it start of the CD drive, and it still wont start linux.

Yes the ISO is still zipped up or whatever, not zipped, but not extracted, ya know...

Help  please![/SIZE]

---

### Post by xmastree on 2005-12-06
Follow these instructions
[http://www.xmastree.34sp.com/ubuntu/burn](http://www.xmastree.34sp.com/ubuntu/burn)
to make your CD from the ISO. If you're not sure, use a CDRW, mistakes are cheaper that way. :rolleyes:

---

### Post by xequence on 2005-12-06
You mean the CD you burned just has the ISO as an ISO file on it, not the contents as it should?

Use Alchohol 120% and click image burning wizard. Then burn the image :)

---

### Post by Abyssal on 2005-12-06
Ok, now I have another problem >.<

When it starts loading it says:
> 
Starting hotplug devices...


and then it sits there for like 20 minutes and then I had to stop it because it woudlnt stop.

---

### Post by xmastree on 2005-12-06
I had that problem with 4.10 and I found it was my card reader (USB). Unplugged it and it was fine.

I think you can use Ctrl-C to skip that (and any other) step if it seems to hang there.

---

### Post by Abyssal on 2005-12-07
Nope, still won't work.

CTRL + C doesn't skip it. Should I just try another distro?

---

### Post by kingsidy on 2005-12-07
xmastree is right. try to unplug all of the necessary usb devices, Some bios have a problem with that. And give it another shot. Or try booting with the acpi off.
As far as trying another distro it is all up to you. Do you want to really give ubuntu a try?

---

### Post by mgmiller on 2005-12-08
You can also try going into your BIOS and turning off/disabling legacy USB support.  I have also heard from several other users about not having a USB card reader plugged in while doing the install.  You can plug it back in after the install is done.

---

