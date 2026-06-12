---
title: "What is this dev/sda1 stuff???"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by chimchim on 2008-04-01
I am learning to use Ubuntu 7,10 and about every two weeks or so I get a message "dev/sda1 mounted 27 times without check - check forced.".
I then have to wait while it does its thing and eventually boots.

What is going on here and should I be worried about it?

Everything works OK once it has booted.

Have a nice day.

---

### Post by xeth_delta on 2008-04-01
/dev/sda1 is probably the partition where Ubuntu is installed on your computer. It is checked every certain number of boots just to check for any eventual problem in the file system. As far as I know it is normal, no need to worry about it.

[EDIT] /dev/sda1 is a special device file that represents the first partition (hence the one) of the first HDD ( hence the a ). IIRC for serial ATA and SCSI devices an "sd" is associated, while for parallel ATA a "hd".

---

### Post by sayakb on 2008-04-01
In your case, /dev/sda1 is the HDD that has the root &quot;/ mountpoint&quot; files for Ubuntu. There is no need to worry about. It's a routine check Ubuntu does. 

EDIT: You might install AutoFsck from here:[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck) 
You can change the number of reboots after which the disks would be checked.

---

### Post by forrestcupp on 2008-04-01
It's kind of like chkdsk in Windows, only in your case it does it every 27 times you boot.

I just leave my computer on most of the time, so I don't get that very often.

---

### Post by chimchim on 2008-04-01
Many thanks Xeth_delta and LinuxIs Innovation for the prompt response.
That is one problem less:)

---

### Post by chimchim on 2008-04-01
And thanks to you too forrestcupp. Have a nice day.

---

### Post by xeth_delta on 2008-04-01
> **chimchim said:**
> Many thanks Xeth_delta and LinuxIs Innovation for the prompt response.
That is one problem less:)

You're welcome! Feel free to ask any further questions you might have.

---

