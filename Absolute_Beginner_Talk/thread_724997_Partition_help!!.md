---
title: "Partition help!!"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by Fraser from Scotland on 2008-03-15
Hello, I needed more space on my windows partition, so I booted up the livecd and Gparted and reduced the size of the ubuntu partition, that all went fine. Then, when it started checking the windows partition it came up with an error and I am not able to resize it. This is incredibly annoying as I have 50gbs of free space on my HD that I can't put to use because of this. 

I seen this on another thread, should I try running it?

```
chkdsk /F c:
```

---

### Post by Terry of Astoria on 2008-03-15
```
chkdsk /F c:
```to my knowledge starts chkdsk to check the C: drive with a full test.

---

### Post by Fraser from Scotland on 2008-03-15
ok, ive got to restart to do the checkdisk. After that I'll try resizing again, thanks.

---

### Post by Fraser from Scotland on 2008-03-15
Ok, I ran the chkdisk and got that finished, then I went onto the livecd (which I am on now btw) and opened Gparted. In gparted it shows my windows partition to have 80gb and there is no free space available, but in reality my windows partition only has 30gb and there is 50gb of free space. Since gparted thinks there is no free space I have no idea how im going to edit my partitions. please help this is very frustatiing.

---

### Post by bumanie on 2008-03-15
Are you using xp or vista?

---

### Post by Fraser from Scotland on 2008-03-15
I'm using XP.

Also, will reinstalling windows remove Ubuntu?

---

### Post by bumanie on 2008-03-15
Can't explain why gparted is not working as you are using xp. Gparted does have some issues with vista, but not xp (as far as I know). 
Reinstalling windows won't get rid of your ubuntu install as long as you ensure you only format the partition or drive that windows is on now. You will however have to reinstall grub from the live cd once windows had been installed as it will overwrite the mbr and won't acknowledge that ubuntu is there.

---

### Post by Fraser from Scotland on 2008-03-15
Ok, but if I wanted to get rid of ubuntu altogether (I am having ubuntu on my desktop, and keeping xp on my laptop, which im using just now) will doing a fresh install of windows go over and remove all of ubuntu?

---

### Post by Moop on 2008-03-15
If Gparted shows the XP partition as 80gb then maybe the problem is with XP recognizing the extra space. Have you looked at your partitions in XP? Control Panel-Administrative Tools- Computer Management-Disk Management.

---

### Post by Fraser from Scotland on 2008-03-15
Windows is seeing it as 80gb as well. Is there any remedy to this?

---

### Post by Fraser from Scotland on 2008-03-15
Ok, new question.

If I reinstall Windows XP will Ubuntu and all the partitions be restored to what they were and will ubuntu be gone?

---

### Post by Fraser from Scotland on 2008-03-15
argh! please help! This is soo annoying! :( all i want to know is If I reinstall Windows XP will Ubuntu and all the partitions be restored to what they were and will ubuntu be gone??

---

### Post by sandysandy on 2008-03-16
if u re-install XP, ubuntu will not be gone.

only the MBR will be overwritten by XP.

to restore GRUB have a look at this link

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

alternately u can use Super Grub Disk.

if u want that ubuntu should be gone during windows installation format the relevant partitions.partitions can also be formatted to NTFS (windows) using gparted live CD.

regards

---

