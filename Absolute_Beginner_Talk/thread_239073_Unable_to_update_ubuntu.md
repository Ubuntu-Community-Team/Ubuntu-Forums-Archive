---
title: "Unable to update ubuntu"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by Eversion on 2006-08-18
I am on my third install of Ubuntu i have windows 2000 pro on another partition so dual boot.The first time i tried Ubuntu my windows was using FAT and everything worked fine but i felt i messed up my install by screwing around.I then reformatted everything including windows this time using NTFS and the installer crashed so i went back to FAT, install went fine.Does it make a difference using FAT or NTFS?

My main problem is i cannot seem to update my Ubuntu it is stating i have 163 updates available,so i click and enter my password..the same pass i use to log in.It says it is the wrong pass and at this point i am really confused.

I then opened the terminal and typed sudo pswrd: changed my pass run the update and nothing runs.. i dont get the wrong pass screen this time though.

I also tried sudo apt-get update,i do get some action doing this but my number of updates still doesnt change.

I would really appreciate help,thank you for your time.

Windows 2000 pro
Ubuntu 6.06 x386.iso
P 350 mhz/384mg RAM
10.3G hd partitioned 6g for ubuntu 4g for windoz

---

### Post by Klaidas on 2006-08-18
Hmm, maybe you just enter a wrong password? Is CAPS LOCK off? :-k

Or in terminal, deos it work?
> sudo apt-get update
sudo apt-get upgrade

the upgrade thing is needed too :)

---

### Post by taurus on 2006-08-18
You will run into deep trouble if you use fat32/vfat filesystem for Linux!!!  If you want to share files between your Windows 2000 and Ubuntu, create a separate partition with fat32 filesystem so both can write to it.  But for Ubuntu, better use ext3 for all of your partitions...

---

### Post by Eversion on 2006-08-18
Thanx for the help guys,really appreciated.the apt-get upgrade worked fine.I think i will go with NTFS as you suggested.

---

### Post by Cone on 2006-08-18
Just to hopefully avert a HUGE danger, he's saying to go with ext3 for any partitions that are just for Ubuntu, have NTFS with Windows (which it will already be), and use FAT32 JUST for the partition that both Windows and Ubuntu are going to be accessing.

Linux lacks the capability to write to NTFS filesystems as well right now (well, that's being changed, but generally).

So...
Ubuntu partition(s): Ext3
Windows partition(s): NTFS
Shared partition(s): FAT32

Hope I helped :S

~Cone

---

