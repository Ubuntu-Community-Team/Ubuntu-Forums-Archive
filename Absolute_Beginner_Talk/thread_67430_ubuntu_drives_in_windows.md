---
title: "ubuntu drives in windows"
date: 2005-09-20
forum: Absolute Beginner Talk
---

### Post by a8o on 2005-09-20
been using ubuntu for a few weeks now, very impressive. i've had to come back to windows xp for a bit and want to access my mp3s, stored on my ubuntu formatted drive. the drive no longer shows up in my computer.

is there a process (in either OS) that i can use to do this?

---

### Post by mozz on 2005-09-20
If you want to access your Ubuntu (ext2, ext3 formatted) drive in Windows you need specific device drivers, like these: [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html) (that's the one I use) ,[http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm)

---

### Post by davmac on 2005-09-20
If your Ubuntu partitions are formatted using ext2 or ext3 then a windows program called explore2fs will let you read them.

Have a look at [http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)

Regards,

Dave Mac

---

### Post by a8o on 2005-09-21
Great replies. THanks

---

### Post by 23meg on 2005-09-21
for full and reliable read/write access to reiserfs and ext3 partitions i recommend Paragon Mount Everything.

---

### Post by a8o on 2005-09-21
In Ubuntu I find i cannot write to my windows drive as well, is that the program i need?

---

### Post by xmastree on 2005-09-21
[QUOTE=a8o]In Ubuntu I find i cannot write to my windows drive as well, [/QUOTE]Linux can't write to a Windows ntfs partition, but it's ok with FAT32. 

The best thing is to make a FAT 32 partition somewhere to share data between the two.

---

### Post by Benzima on 2005-09-28
I'm alittle confused. 

Is it better to have some space partitioned as ext2 in Ubuntu and use the fs-driver to give Windows access to the linux partition, 

or 

format that space as vFAT 32, which gives Ubuntu read & write access?

or are they about the same?

Thanxxx in advance.

No longer confused. The fs driver thingy makes it a snap.

---

### Post by a8o on 2005-10-02
[QUOTE=xmastree]Linux can't write to a Windows ntfs partition, but it's ok with FAT32. 
The best thing is to make a FAT 32 partition somewhere to share data between the two.[/QUOTE]

My fault, i didnt express myself as well as i should have.

Can i write to my linux partition in windows?

---

### Post by Snocrash on 2005-10-11
[QUOTE=a8o]My fault, i didnt express myself as well as i should have.

Can i write to my linux partition in windows?[/QUOTE]

explore2fs can write to them....usually

 -Sno

---

