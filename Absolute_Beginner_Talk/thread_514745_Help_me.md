---
title: "Help me"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by ctrlaltphreak on 2007-08-01
Yesterday I booted up the latest ubuntu live cd and double clicked install. This took me to the partitioner were I chose the size of the partition I wanted then went ahead to install the OS. Everything seemed to have gone well ending with a messgae informing me to reboot and remove the live cd. I did this but whilt rebooting my machine stopped with a "error loading operating system" message. Any idea what happened/how to fix it?

---

### Post by mathewb on 2007-08-01
how did you partition it?

---

### Post by rich.bradshaw on 2007-08-01
You could try using the alternate install CD - what is your hardware - someone else might be able to tell you if your pc should need it.

Alternativly the CD might have errors, you can check it using the menu when you first boot from it.

---

### Post by ctrlaltphreak on 2007-08-01
I'll try booting from the live cd again when I get home. I partioned my 160Gb hard drive telling ubuntu I wanted the new partion to be 60Gb.
One other thing, I originally tried to install ubuntu onto my other 40Gb harddrive but the installation hung at 55% so I hard rebooted back to the live cd and then installed to my main drive but partitioned it. This install hung at 49% but I left it overnight and when I came down this morning it was complete leading me to believe the first install didn't hang at all. Will his affect anythink? Should I disconnect the 40Gb drive and then try booting?

---

### Post by ugm6hr on 2007-08-01
Ubuntu should not take all night to install.... What are your system specs (i.e. RAM / Processor)?

---

### Post by ctrlaltphreak on 2007-08-01
AMB Sempron 3300+ 1Gb RAM. I guess it must be the live cd I had to burn another as the first wouldnt boot (cheap CD-R). I'll burn another if i can boot xp, or can i access my windows partition from the live cd?

---

### Post by ugm6hr on 2007-08-01
> **ctrlaltphreak said:**
> can i access my windows partition from the live cd?

Yes - for the purposes of accessing the .iso file.

---

### Post by ctrlaltphreak on 2007-08-01
Is there burning software included on the live cd. If there is then I can burn it using that? How would I get XP to boot or is this not possible? If not, no problem as long as I can back up my files using the live cd then I'll re-install xp as well to have a dual boot setup.

---

### Post by thefoolisme on 2007-08-01
First off, you're supposed to backup your files BEFORE attempting this stuff.  

Anyways, it sounds as though you have a bad CD burn.  did you check the MD5 checksum after downloading, and run the disk check on the live CD?  If you burned it above 4x you could definitely have errors.  

Using the live CD, open a terminal and type:

sudo fdisk -l (lowercase L)

Post it here, so we can see your disk configuration.  

Do you have an external hard drive to back your windows stuff up to?  If so, you can use the live CD to do that, but you'll probably have to install NTFS-config to do it.  

No sure if you can use the live CD to burn an ISO...I guess if you mounted the windows partition wherever you saved the ISO, you could, but you will still have to use NTFS-config to get to it, I think.  Of course, you'd also have to have 2 CD drives, 1 for the live CD and one for the blank.

---

