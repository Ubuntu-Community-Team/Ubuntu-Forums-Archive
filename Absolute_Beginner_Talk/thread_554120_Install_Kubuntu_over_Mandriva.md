---
title: "Install Kubuntu over Mandriva"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by RogerM on 2007-09-18
I have a laptop with two hard drives with XP and Mandriva install as a dual boot system.  It seems that Mandriva has partitions on both drives.  I would like to install Kubuntu over Madriva WITHOUT touching the XP OS or partition.  

Installing Kubuntu doesn't seem to recognize Mandriva.  

Can someone point me to a procedure to install Kubunto over Madriva without adversely affecting my Windows XP?

Thanks,
  Roger

---

### Post by logos34 on 2007-09-18
Can you post your fdisk?

**sudo fdisk -l **(lowercase L)

You might try thr gparted live cd to format mandriva root, then maybe you'll be able to install kubuntu

---

### Post by CowzRule on 2007-09-18
I'd find out which partitions Mandriva is using then have the installer format and install Kubuntu to those partitions. Then I'd have Grub installed to the mbr and use grub to boot either Kubuntu or Windows.

---

### Post by RogerM on 2007-09-18
> **logos34 said:**
> Can you post your fdisk?

**sudo fdisk -l **(lowercase L)



/dev/hdb5                 approx 5.6G    - Mandriva root
/dev/hdb6                 approx 500K    - swap
/dev/hdb7                 approx 19G      - home   (I would like to keep this, but doesn't really matter)

Roger

---

### Post by RogerM on 2007-09-18
> **CowzRule said:**
> I'd find out which partitions Mandriva is using then have the installer format and install Kubuntu to those partitions. Then I'd have Grub installed to the mbr and use grub to boot either Kubuntu or Windows.

Is the Grub that is already there updated appropriately by the Kubuntu install?

---

### Post by logos34 on 2007-09-18
> **RogerM said:**
> /dev/hdb5                 approx 5.6G    - Mandriva root
/dev/hdb6                 approx 500K    - swap
/dev/hdb7                 approx 19G      - home   (I would like to keep this, but doesn't really matter)


Where's the rest? The other disk? XP?  

> Is the Grub that is already there updated appropriately by the Kubuntu install?

If and when you install kubuntu it will write its own grub to the mbr.

Get the gparted live cd--maybe it will be able to detect everything.  Not sure what the prob is here

---

### Post by RogerM on 2007-09-18
> **logos34 said:**
> Where's the rest? The other disk? XP?  



If and when you install kubuntu it will write its own grub to the mbr.

Get the gparted live cd--maybe it will be able to detect everything.  Not sure what the prob is here

Mostly my ignorance.

I used the manual option in the partitioning to set hdb#5 to /, hdb#6 to swap, and hdb#7 to /home which seemed to work and the Grub was overwritten.

But the installed Kubuntu didn't work.  I get an error saying: "Your saved session type '01KDE' is not valid anymore ..."

After clicking OK a couple of times and logging on I get the message "Could not start kstartupconfig. Check your configuration."

That is as far as it gets.

---

