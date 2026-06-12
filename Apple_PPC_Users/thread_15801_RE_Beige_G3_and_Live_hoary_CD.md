---
title: "RE: Beige G3 and Live hoary CD"
date: 2005-02-16
forum: Apple PPC Users
---

### Post by betterok5 on 2005-02-16
After much twiddling with Bootx parameters and consultations with this forum and posts to the wiki I was finally able to get the hoary live CD to boot on my Beige G3, 300Mhz.  The Bootx settings I used are as follows:
check all 4 option boxes:
Put vmlinux kernal and initrd.gz on "root" level of Mac OS system volume, not in the linux kernal folder.
Set ramdisk to <somemacdiskname>:initrd.gz
Set kernal name to vmlinux.
In parameter space put: init=/linuxrc,chroot/dev/<cdromname>(I used hdc).
The cd then boots into the installer.  
At that point I had my trusty 4.3 gig SCSI external connected so I went ahead and reformatted it using <guided partitioning>.
The installer was unable to complete the install because it couldn't find what it needed to continue.  I finally just quit the process and it rebooted into Mac OS.  
Question:  Is the live cd supposed to only go to the installer or is there a standalone mode that I am missing somehow?  Any input appreciated.
KK

---

### Post by betterok5 on 2005-02-16
Well, at least it worked once.  Subsequent attempts all ended in kernal panic or tried to kiil init.  Back to the drawing board.
kk

---

### Post by trash on 2005-02-17
what i noticed on my g3,266 is that after every failed attenpt to install a complete repartition was necessary otherwise kernel panic everytime.
I haven't tried Hoary yet, but will sometime soon:)
keep me posted.

---

### Post by betterok5 on 2005-02-17
Thanks for your reply.
A complete repartition would not hurt my feelings since that is all I accomplished in the first place.  (I did completely erase a crippled Debian install but no big loss there either.)  What I was hoping to do was run Ubuntu from the live cd and I guess it could be said that I did - at least the installer ran from cd.  
Subsequently I am unable to boot from the cd.  That seems a little strange since the cd should remain unaltered.  Only the Bootx parameters could have been changed.  I have tried a few times to reboot with minor alterations to Bootx but no joy as yet.  
KK

---

