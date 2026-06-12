---
title: "Sharing 2nd drive with samba"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by BillGod on 2007-01-27
I am attempting to share my second hard drive.  I have the share setup and you can access it from my other pc.   The problem comes in when I mount the drive to the directory.  As soon as the drive is mounted you no longer have access from the other computer.  I am mounting the drive in fstab.  Entry looks like this.

/dev/hda1 /home/bill/shared ext3 defaults 0 0

ls -la on that dir looks like this.

drwxr-xr-x  2 bill bill       4096 2007-01-02 19:08 shared


Remember I have read write access from my xp machine until i sudo mount -a and remount the drive.

---

### Post by kosmic on 2007-01-27
I don't know if i understant your problem.

But how can you acess the drive when it is not mounted ??

what do you have in your /etc/samba/smb.conf file ?

---

### Post by BillGod on 2007-01-27
i have  /share  shared with samba.  you have read write access to it from xp.  If I mount my 2nd hard drive to that directory.  you no longer have any access to it.

---

### Post by BillGod on 2007-01-27
smb.conf


[shared]
path = /shared
available = yes
browsable = yes
public = yes
writable = yes

---

### Post by kosmic on 2007-01-27
Try to mount your second hardrive to another directory and then inside the samba share make a softlink to the directory where your 2nd hardrive is mounted and see if it works.

---

### Post by BillGod on 2007-01-27
i have the link created 

bill@Ubuntu-Bill:/shared$ ls -la
total 8
drwxrwxrwx  2 root      root      4096 2007-01-27 20:56 .
drwxr-xr-x 22 root      root      4096 2007-01-27 19:53 ..
lrwxrwxrwx  1 bill      bill        21 2007-01-27 20:56 mp3 -> /home/bill/shared/mp3
-rwxr--r--  1 maranda_l maranda_l    0 2007-01-27 20:14 New Text Document.txt
bill@Ubuntu-Bill:/shared$ 


when you connect in from xp you can see "new text document.txt" and thats it.  link mp3 is not visible.

---

### Post by kosmic on 2007-01-27
try this, in /etc/samba/smb.conf

add this

[TEST]
path = /home/bill/shared <- where your 2nd disk is mounted
available = yes
browsable = yes
public = yes
writable = yes 

Save and exit, and do sudo /etc/init.d/samba restart

Wait 2, 3 minutes so windows can see it and try again

---

### Post by kosmic on 2007-01-27
Did it work ??

---

### Post by BillGod on 2007-01-27
that was the first thing i did.  you cannot even access the share at all.

[mp3]
path = /home/bill/shared/mp3
available = yes
browsable = yes
public = yes
writable = yes

---

### Post by kosmic on 2007-01-27
> **BillGod said:**
> that was the first thing i did.  you cannot even access the share at all.

[mp3]
path = /home/bill/shared/mp3
available = yes
browsable = yes
public = yes
writable = yes

Just a silly question, and you can browse that disk in ubuntu ?? without using samba ?? If you go to /home/bill/shared/ in nautilus can you see the contents of the drive ??

---

### Post by BillGod on 2007-01-27
yes i play all my mp3's from that directory every day

---

### Post by kosmic on 2007-01-27
Hum very strange, the only thing i can say is to look at the log files to see what is hapening.

/var/log/samba/smb*

---

### Post by BillGod on 2007-01-27
just so i myself nor anyone else thinks I am crazy.  I mounted my second drive on my other ubuntu box and tried to share and connect to it. i get the exact same results on that one.

---

### Post by BillGod on 2007-01-28
bump up for another day of trying.

---

### Post by kosmic on 2007-01-28
I have to admit it is a very strange problem.

Just for curiosity what your /var/log/samba/log.smbd says ??

---

### Post by BillGod on 2007-01-28
its empty

---

