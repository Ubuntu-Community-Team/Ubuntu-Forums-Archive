---
title: "Bootup Issues.Please help"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by linux phreak on 2007-12-17
Hi friends.I recently managed to install ubuntu 7.10 and i dont have XP anymore.The install went smoothly assisted by some good people over here.I have the machine running smoothly now.The problem is that the boot sequence is set to boot from CD in bios.After the install i went there and changed it to hdd0.But if i do that ubuntu will not boot but show a black screen.Then i turn it to boot from CD and it works fine.I have two hard drives.Ubuntu is on a 40 gb drive full.The other one is 160gb and is NTFS.How can i rectify this?

---

### Post by PmDematagoda on 2007-12-17
Change the Boot Device priority of the HDDs to the second one, then try booting from that hard disk.

---

### Post by linux phreak on 2007-12-17
But that disk has important data on it.Will there be any harm to the data?

---

### Post by PmDematagoda on 2007-12-17
None at all, just changing the boot device priority of the HDD does not harm it.

---

### Post by linux phreak on 2007-12-17
ok so i have to change the sequence to hdd1 right?.Is there a way i can edit this from ubuntu itself without restarting?

---

### Post by PmDematagoda on 2007-12-17
You cannot edit the BIOS using Ubuntu, you will have to enter the BIOS when booting the PC. One question though, have you used the BIOS before?

---

### Post by linux phreak on 2007-12-17
yes i know, that blue screen you get when you frantically press del button during boot

---

### Post by PmDematagoda on 2007-12-17
Yes, go to the Boot section of the BIOS and then change the Boot Priority of the hard drives to the second hard drive.

---

### Post by linux phreak on 2007-12-17
Hi i did that and restarted and it worked.Then i shut the system down then started it.The ubuntu did not load it showed that black screen again.

---

### Post by linux phreak on 2007-12-17
please help me im a novice

---

### Post by linux phreak on 2007-12-17
The another problem that i face is that the wallpapers i set are not there wheni restart. All i see is a brown background.The default wallpapers work though.The rythm box also seems to be unable to store my music and after a reboot when i click on a song it quickly begins to remove every thing in the library.

---

