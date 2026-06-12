---
title: "Too Much Customization"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by dannymichel on 2007-06-15
I'm afraid...I'm afraid because I have done ALL this customizing to my Ubuntu installation and applications and I'm afraid of an upgrade. Think I should be or is there an easy way for me to ease my fear?

---

### Post by NeoLithium on 2007-06-15
Well, that depends. What are you upgrading To/From?   Generally it goes ok, though I always recommend that things are backed up anyway because accidents do happen here and there.

---

### Post by 67GTA on 2007-06-15
It would be better to save your home folder, make an APT ON CD for use as an extra repository for your new installation, and just download,burn and do a clean install. I have never had an upgrade go right.

---

### Post by Nekiruhs on 2007-06-15
Really, I've never had one go wrong, odd.

---

### Post by 67GTA on 2007-06-15
EDIT:I've had two fail because of "customizing". It really depends on what you have customized. The first one from Warty to Dapper went fine because I left Warty alone. LOL

---

### Post by AusIV4 on 2007-06-15
> **Nekiruhs said:**
> Really, I've never had one go wrong, odd.
I've never had one go right. Dapper to edgy left my system unbootable - I later learned that I could have reconfigured Xorg and everything would have been fine, but it was too little too late.

Edgy to Feisty was rather bizarre. Every time my system booted up, I'd be thrown to a root terminal with the instructions: "Apt-get not found. Type apt-get install apt to install" - Typing exit would send me to the desktop, but it was rather obnoxious. I later found out this was because my /etc/fstab file referred to disks as /dev/hd*, while feisty had renamed them /dev/sd*. Again, by the time I figured this out, I'd already formatted and done a fresh install.

I always recommend that people use a separate home partition. Reinstalling Ubuntu is a 30 minute ordeal - I pop in the CD, format my root partition, install on the newly formatted partition pointing /home/ to the home partition. Once it's booted, I run updates and install a few programs I use frequently. While this means there's no real risk to trying an upgrade, I find things go more smoothly if I just do a clean install.

I might also note, I have a 60 GB hard drive. I have two 5 GB root partitions, 48 GB home, and 2 GB swap. Usually when I do an upgrade, I'll do it to whichever 5 GB root partition I'm not using much at the time. That way if anything goes wrong, I can just revert back to a stable system with a few changes in grub.

---

### Post by dannymichel on 2007-06-15
Can someone give me some command line so I can backup my ~/ directory onto my /media/sda1 directory?
NEWB here

---

