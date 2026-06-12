---
title: "Total Linux noob... please help a guy out..."
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by omegagames on 2006-11-17
Okay, so I've been going through this tutorial: [http://www.pcmech.com/show/os/903/3/]("http://www.pcmech.com/show/os/903/3/")

This is my system as of now:
P4 3ghz processor, 1GB Ram
80GB SATA HD (Came with system, windows is here)
250GB IDE HD - stores files
250GB IDE HD Installed on a PCI RAID controller - also just stores files (I only have one IDE Channel, hence the RAID Card)
250GB SATA HD (Brand spankin new)

What I want to do is give 60 or so odd gigs to Ubuntu (ver 6.10 I believe) on the new SATA HD.  So I created partitions for "\" "swap" and "\home".  I didnt know what the other options ("\usr" "\var") were and since they weren't in the tutorial I didn't add them.  I got an installation successful screen and shouted Hip Hip Hooray.

Upon rebooting, I thought I would see a screen that asked me to choose my OS pleasure, but good ol' Windows done booted itself up.  This made me frown, so as my solution, I disabled my first SATA port in my Bios and tried again.  This time I got "Grub Loading stage 1.5. Error 21" and had to Ctrl-Alt-Del myself to safety.  I don't know if it's me disabling my primary HD that is causing the error, but if its enabled I can't run Ubuntu.

Now I'm not a computer noob by any means, but when it comes to the intricacies of installing an Operating System, I feel like the time my grandmother tried to play Halo 2 on Live.  So any help is definitely appreciated...

---

### Post by bodhi.zazen on 2006-11-17
You need to install GRUB into the MBR (master boot record)

[Restore GRUB](http://doc.gwos.org/index.php/Restore_Grub)

---

### Post by ciscosurfer on 2006-11-17
> **bodhi.zazen said:**
> You need to install GRUB into the MBR (master boot record)

[Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub")These also help:
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

