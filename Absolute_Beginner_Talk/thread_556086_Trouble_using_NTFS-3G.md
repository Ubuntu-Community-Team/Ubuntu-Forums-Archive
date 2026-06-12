---
title: "Trouble using NTFS-3G"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by Richard 3838 on 2007-09-20
I am using Kubuntu over Feisty 7.04. I have a 160GB HD with 2 approximately equal partitions. The first has XP on the second my Ubuntu. I also have another external HD (80GB) which is NTFS , as is my XP partition.
I install NTFS-3G and NTFS configure  and here is my problem. I cannot activate write on only one of the NTFS partitions, nor can I unactivate one. I have to do them both or none. The flags on "NTFS configure" show either internal (XP) or external activated but the permissions for the icons showing the drives, on the desktop follow the last operation involving both drives. What I have had to do is activate write to both drives, then go to the command line and umount the XP one. If I leave the system and shut it down, when I reboot, I have to go through this again.  I am using the external NTFS drive as a common filing place and really don't want the XP Partition accessible at all from Kubuntu.
Either there is a bug in NFTS-3G or I am doing something wrong.
Any suggestions?  TIA
Richard

---

### Post by Pumalite on 2007-09-20
Post from Kubuntu Terminal:
sudo /etc/fstab

---

### Post by meierfra on 2007-09-20
> Post from Kubuntu Terminal:
sudo /etc/fstab

He meant:  cat  /etc/fstab

---

### Post by Pumalite on 2007-09-20
You are right. Sorry for the typo.

---

### Post by Richard 3838 on 2007-09-20
> **Pumalite said:**
> You are right. Sorry for the typo.


Need more info.

---

### Post by Richard 3838 on 2007-09-20
> **Richard 3838 said:**
> Need more info.

"no such file......."

---

