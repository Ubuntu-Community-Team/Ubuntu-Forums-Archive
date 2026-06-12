---
title: "XP install after UBUNTU, and partition problems"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by kingkykat on 2007-04-24
First, I have 2 Hard Drives.  Currently my sda is botched up from previous ubuntu removal and reinstall to the sdb.  

On the SDA I want to set up vista (i have the upgrade edition) so i need to first install XP to it.  When I reboot with the XP cd in the drive, the blue text based screen comes up, copies files for install, then I tell it to format the C drive (have tried both full and quick formats).  after that, the computer restarts, and copies install files again, (same as at the beginning) and then comes to the options to format again.  I am stuck in this circle.  I somehome screwed up this drive.

I have tried booting with live ubuntu cd and using GParted to repartition the hard drive, but when I do, I notice that at one portion it fails and brings of a folder of garbage left over from previous ubuntu install.  Partition and format will not just overwrite and get rid of this stuff?

Also, is it my MBR that is somehow screwed up and will not let XP to proceed?

Please help, running out of hair to pull out.

---

### Post by old_geekster on 2007-04-24
If it were me in your place, I would do a clean install of both XP and Ubuntu.  I would install XP first, then install Ubuntu.  Ubuntu will recognize the fact that XP is installed and setup GRUB accordingly.

It sounds to me like you definitely have some corruption somewhere.

---

### Post by kingkykat on 2007-04-25
Thanks, but the problem doesn't seem to be at all related to ubuntu as it is on a totally separate physical hard drive (what would be D in windows).

I am trying to clean install win XP on the what was the C drive in Windows, which is where I am haveing the problems listed above.

Any Ideas anyone???  How can I even clean install XP if it keeps doing this, trying to figure out what ubuntu has done to my drive.  Is it something in the bootloader?  I dont think so because with an xp install disk in the drive, I would think it would ignore that anyways.

Also, sometimes a Lost and Found CD with an X shows up on C from the ubuntu live session.  I am unable to view the contents or delete it, although sometimes randomly it seems, when I run GParted and tell it to do something to the C drive, it opens up the folder lost and found and I see what is left in there (this opens after sellecting format, and then clicking apply.  And it will not complete the operations.

Thanks for any help!!

---

### Post by totalnub on 2007-04-25
sounds like a prob with the partitions not being formatted? i have a CD that is similar to gparted, but it forces the selection you've made. I had to do this to shrink my ntfs partition.....damn bad sectors lol.

let me know if you would like me to upload it.

---

### Post by totalnub on 2007-04-25
ok well here is the .iso if you want it. it is very small, 1.5MB.
sorry, the forums don't allow me to attach, but i put it up on my own webspace.
[www.eng.fsu.edu/~bielacl/parteditor.iso](www.eng.fsu.edu/~bielacl/parteditor.iso)
hope this helps :)

---

### Post by kingkykat on 2007-04-25
Thanks!  I will try this out when I get home from work in a few hours.

---

### Post by kingkykat on 2007-04-25
Thanks that program worked great!!! Problem solved, vista is back up online.  Now I just hope I can get it to dual boot without haveing to try all this for a 4th time.

---

