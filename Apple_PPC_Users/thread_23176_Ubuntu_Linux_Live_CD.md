---
title: "Ubuntu Linux Live CD"
date: 2005-03-31
forum: Apple PPC Users
---

### Post by octavedoctor on 2005-03-31
I downloaded the ISO disc image of the PPC live CD distro and duly burnt it as an ISO 9660 CD but my iMac wouldn't recognise it as a bootable volume. I tried Toasting it as a Mac/PC disc, but still no dice. What am I overlooking?   

I'm sure I'm being an idiot somewhere so go easy on me...  

Apologies if this turns up as a duplicate post I posted it last night but it doesn't seem to have manifested anywhere.... :-?

---

### Post by Leonida on 2005-03-31
Burn as Disk image, don't use DiskUtility

[PPCwiki- how to burn ISO image](http://ubuntuppc.webplazahosting.com/index.php?ISO%20Image)

---

### Post by octavedoctor on 2005-03-31
[QUOTE=Leonida]Burn as Disk image, don't use DiskUtility

[PPCwiki- how to burn ISO image](http://ubuntuppc.webplazahosting.com/index.php?ISO%20Image)[/QUOTE]

thanks for the link, I found that disk utility crashed if I tried to burn the .img file from the app.. 

I'll try that.

---

### Post by Leonida on 2005-03-31
[QUOTE=octavedoctor]thanks for the link, I found that disk utility crashed if I tried to burn the .img file from the app.. 
I'll try that.[/QUOTE]
Try Fire Starter FX, pherhaps is a little bit easyer than MissingMediaBurner.

---

### Post by octavedoctor on 2005-03-31
OK, I followed that link, and downloaded firestarter. It burned a CD, but this was exactly the same as the one I burned using Toast. No bootable function. Startup disk selector doesn't recognise it as a bootable volume.

Any other ideas anyone?

---

### Post by Down8ve on 2005-03-31
I used our Windows PC to do it since Disk Utility didn't wish to do it.

DSM

---

### Post by matgorb on 2005-03-31
Firestarter here, drag and drop the file in it, waited a bit to burn, restart hold C and the cd booted fine, so....

---

### Post by octavedoctor on 2005-03-31
I just tried booting from the CD mac-style by holding down C after the startup chime; that worked a treat! after logging  out of Linux however the iMac didn't boot straight back into OSX, but into OS9 first. i then had to reset the startup disc from within OS9 and reboot into X. Thanks for the help all!

I didn't like the Gnome desktop; I didn't feel it was as intuitive as K, nor as flexible in control of appearances. I'm so used to silky smooth fonts everywhere on the mac that even with font-smoothing enabled the  fonts in the menus and title bars looked jaggy. Perhaps there are ways of configuring it of which i'm ignorant. Nor could I access the Macs internal drive and filesystem from the desktop or workout how to get it to mount  the internal drive as a volume. I had  the same problem on a PC using @tmission, but not Knoppix which allowed me to browse the PCs filesystem quite happily. 

Hmmm... :-k

---

### Post by matgorb on 2005-04-01
Well, the way I use the Live CD, as demo for my research about linux use, i prefer it not to allow access to the drive...just so people do not hold me responsable for crashing their system, i guess it might be the live ubuntu philosophy, if you mount something, then you know what you are doing so you take reponsability.


mat

---

### Post by Leonida on 2005-04-01
[QUOTE=octavedoctor]I didn't like the Gnome desktop; I didn't feel it was as intuitive as K, nor as flexible in control of appearances.
.....[/QUOTE]
Try [Kubuntu](http://www.kubuntu.org.uk/) live CD.

---

### Post by ubuntubrian on 2005-04-08
I would also like to mount my hd on the gnome desktop and access my files on it. When Ubuntu boots fromthe cd it shows as detecting airport and the modem but I cannot for the life of me figure out how to set up my network settings to use either. Is there a decent tutorial that will walk me through the setup? I'm spoiled with Panther's ease (I just configured my wife's new ibook). Do I need domain addresses and all of that arcane stuff and why won't ubuntu autodetect my modem port? How do I enable Airport to get online? so many questions and I so want to get moving toward linux (now a fink user, which is great except their packages tend to be a bit outdated). I have resisted repartitioning my hd and installing ubuntu there so I really want the live cd to work for me. I see many other posters who use the ;ive cd as their distro and it seems ideal-for now.
G4 TiBook 15"
Panther 10.3.8
1Ghz
784Mb ram
superdrive

---

