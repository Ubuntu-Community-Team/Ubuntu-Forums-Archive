---
title: "[SOLVED] Amarok won't play CDs"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by Mansfieldatron on 2008-01-13
I'm running Amarok, using the xine engine, under GNOME. I have two disc drives on my box; one DVD-RW and one CD-RW. 

When I insert an audio disc into the CD-RW drive, GNOME recognizes it, it appears on the desktop, and Sound Juicer pops up with it's contents. When I Engage>Play Audio CD in Amarok, a text box at the bottom left comes up with "Could not read AudioCD".

 I've gone into Settings>Configure Amarok>Engine, and changed the default device under Audio CD Configuration from /dev/cdrom, to /media/cdrom, to /media/cdrom0, to /cdrom, and back to /media/cdrom. Amarok still does not play the cd. I've installed kdemultimedia-kio-plugins, nothing changed. 

Any remedies? Is it just a side effect of running a KDE app on GNOME?

---

### Post by nikoPSK on 2008-01-13
Although this isn't really an answer to your problem, but you can play cd's in totem too. (Applications->Sound & Video->Movie Player

And I doubt it would be because of running a KDE app in gnome.

Best,
nikoPSK

---

### Post by logos34 on 2008-01-13
> **Mansfieldatron said:**
>  I've gone into Settings>Configure Amarok>Engine, and changed the default device under Audio CD Configuration from /dev/cdrom, to /media/cdrom, to /media/cdrom0, to /cdrom, and back to /media/cdrom. Amarok still does not play the cd.

no, you want either **/dev/hdc** or** /dev/hdd**. I'm assuming they are connected to the standard IDE location--secondary master and slave.  Change to hda or hdb if they're on the primary channel.  (A quick look at **/etc/fstab** will show how the drives are recognized).

They might also be listed as ** /dev/scd0** or **/dev/scd1**.

---

### Post by Mansfieldatron on 2008-01-13
> **logos34 said:**
> no, you want either **/dev/hdc** or** /dev/hdd**. I'm assuming they are connected to the standard IDE location--secondary master and slave.  Change to hda or hdb if they're on the primary channel.  (A quick look at **/etc/fstab** will show how the drives are recognized).

They might also be listed as ** /dev/scd0** or **/dev/scd1**.

/dev/scd0 worked.

The problem with Amarok is fixed, but now when it gets to "populating playlist", the CD-RW drive revs over and over and it doesn't do anything. That's probably a hardware problem though.

Thanks!

---

### Post by logos34 on 2008-01-13
> **Mansfieldatron said:**
> /dev/scd0 worked.

The problem with Amarok is fixed, but now when it gets to "populating playlist", the CD-RW drive revs over and over and it doesn't do anything

ok, super.  Umm, do the CD tracks appear in the playlist windows?  I have a problem with the CD not looking up the cd on freedb right away...takes forever and I have to actually click on each one before it fetches the track title.

---

### Post by Mansfieldatron on 2008-01-13
> **logos34 said:**
> ok, super.  Umm, do the CD tracks appear in the playlist windows?  I have a problem with the CD not looking up the cd on freedb right away...takes forever and I have to actually click on each one before it fetches the track title.

Well, it just worked now. So whatever the problem was cleared up.

Thanks a lot for your help. Much appreciated.

---

### Post by logos34 on 2008-01-13
Mark as 'Solved'.  (>thread tools)

---

