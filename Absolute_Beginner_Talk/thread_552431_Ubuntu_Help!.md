---
title: "Ubuntu Help!"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by Tootles on 2007-09-16
Ok my cd never boots while i have ubuntu installed, it boots on my other cpu
it sais press any key to boot cd, but i do and nothing happens
is there a way to uninstall ubuntu in terminal?
and can i still boot a cd without an os?

---

### Post by limbourg31 on 2007-09-16
Yes you can boot a cd without an os. Removing ubuntu in the terminal is unadvisable. The best thing to remove ubuntu would be to just delete the entire partition through gparted, but make sure to back up that data.

---

### Post by jordanmthomas on 2007-09-16
> **Tootles said:**
> 
and can i still boot a cd without an os?
Certainly

---

### Post by Tootles on 2007-09-16
how do i open gparted, i do not know where it is

---

### Post by peabody on 2007-09-16
> **Tootles said:**
> Ok my cd never boots while i have ubuntu installed, it boots on my other cpu
it sais press any key to boot cd, but i do and nothing happens
is there a way to uninstall ubuntu in terminal?
and can i still boot a cd without an os?

???????? WHA???

Be coherent man.  We can help you, but seriously, your post is nothing but confusing...are you saying that ever since you installed Ubuntu you couldn't boot your windows CD?  I'm guessing this because windows cds normally say "press any key to boot from cd".  Is this the case?

---

### Post by Tootles on 2007-09-16
yes it is

---

### Post by Tootles on 2007-09-16
it wont boot the windows cd..

---

### Post by Tootles on 2007-09-16
?

---

### Post by st33med on 2007-09-16
Please don't bump every minute. Anyway, go to this site:
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")
And burn the image on a CD. Reboot with the CD in the computer.

---

### Post by Tootles on 2007-09-16
why would i burn gparted to a cd?
what does it do

---

### Post by Tootles on 2007-09-16
nvm, but i still want an answer about windows cd not booting..

---

### Post by peabody on 2007-09-16
holy crap!  patience grasshopper!  this ain't IRC.  Please try to be descriptive.  When you press a key on the keyboard while trying to boot the Windows CD, what exactly happens?  "it doesn't work" is really, REALLY not descriptive.  What happens?  Blank screen?  What?

---

### Post by Tootles on 2007-09-16
sais cd rom found
press any key to boot cd
i press keys, but it doesnt even saying anything, it just stays the same
then it just loads ubuntu

---

### Post by peabody on 2007-09-16
> **Tootles said:**
> sais cd rom found
press any key to boot cd
i press keys, but it doesnt even saying anything, it just stays the same
then it just loads ubuntu

(FYI, sais is spelled "says")

Sounds like keyboard input isn't reaching the bootloader on the cd.  Can you use the keyboard to get into your bios?

---

### Post by st33med on 2007-09-16
> **Tootles said:**
> why would i burn gparted to a cd?
what does it do

If you want to uninstall Ubuntu, it is best to erase the Ubuntu's partition. ext3 is the partition.

Is your BIOS set up to have the CD boot first? Or, is there a key that you can press on boot-up that helps you choose what you want to boot from? If so, press that key *rapidly*.

---

### Post by Tootles on 2007-09-16
yes it has cd-rom boot first
and where it sais press any key to boot, i pressed it rapidly but nothing

---

### Post by peabody on 2007-09-16
> **st33med said:**
> 
Is your BIOS set up to have the CD boot first? Or, is there a key that you can press on boot-up that helps you choose what you want to boot from? If so, press that key *rapidly*.

If he's seeing the message I think he's seeing, his machine is booting from the CD.  The bootloader on windows install disks checks the harddrive to see if an OS is already present and if it is, it doesn't boot from CD without user intervention.  It was designed that way so simple-minded users who install windows and forget to take the disk out after installation don't end up back at the install inadvertently running through it again.

---

### Post by Skidpad on 2007-09-16
Will it boot from any other cd? (ie, are you sure your Windows cd is good)

---

### Post by Tootles on 2007-09-16
yes its good, it works on my other cpu, and ubuntu cd's work

---

### Post by Skidpad on 2007-09-16
> **Tootles said:**
> yes its good, it works on my other cpu, and ubuntu cd's work
Sorry - just realized you said that at the beginning.

---

### Post by Tootles on 2007-09-16
i only have ubuntu installed, but the xp cd never boots..

---

