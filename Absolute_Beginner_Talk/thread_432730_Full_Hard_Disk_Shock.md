---
title: "Full Hard Disk Shock"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by faust99 on 2007-05-04
Almost had a heart attack when, on trying to log into Ubuntu, I received an error telling me that since my hard disk was completely full, I would not be able to log in and should therefore contact my administrator!:? 

Prior to this, I had tried moving a large file from an external hard drive onto my internal one, and inadvertently filled up the drive completely.

I was just thankful that 30 minutes before I had been reading about how to manipulate files from the terminal, and with this still relatively fresh in my mind I managed to start the computer in recovery mode and delete the offending file from the terminal to leave some space on my hard drive and be able to log in. :idea:\\:D/ 

The moral of the story for uber newbies like me: don't fill your hard drive to capacity, and it definitely makes sense to know the basics of operating the terminal.

Now for that stiff drink  :lolflag:

---

### Post by Cypher on 2007-05-04
Good thing you managed to recover, it is always wise to do "df -h" before/during and after any large file copies to ensure that no partition is approach it's limit. Paritioning properly is key to ensuring that this sort of thing never happens..

..and pass me a drink too! :)

---

### Post by vanadium on 2007-05-04
That is one advantage of having a separate partition for /home. (nevertheless, I do not have this ...)

---

### Post by candtalan on 2007-05-04
I  have read that linux reserves somehow a small amount of space for the root user which allows system (root) function in such user emergency.

---

### Post by faust99 on 2007-05-05
> **Cypher said:**
> Paritioning properly is key to ensuring that this sort of thing never happens..

Do you mean creating a separate partition for /home?

---

### Post by k5787 on 2007-05-13
hello....i was just wondering that when your hard disk is full particualy the home folder how do you delete files in there so as to log in when you cant in the first place

---

### Post by Nekiruhs on 2007-05-13
> **k5787 said:**
> hello....i was just wondering that when your hard disk is full particualy the home folder how do you delete files in there so as to log in when you cant in the first place
Single User/Recovery mode from the grub menu gives you a fullscreen root terminal. You can delete it from there by using 
```
rm /path/to/file/to/be/deleted.etc
```

---

### Post by k5787 on 2007-05-13
thanks im going to try that right

---

### Post by nonewmsgs on 2007-05-13
can you move your /home ?

---

### Post by k5787 on 2007-05-13
i was able to delete the folder that had the excess files. it was a folder that i created called video and i had some avi. files in there. im able to log in the system now with out a problem. I never thought this could happen using this os. When I installed fiesty i did so with a fresh installation, it just shocked me how fast the disk space had went. Is there a way for disk compression on ubuntu or something.

---

### Post by k5787 on 2007-05-13
I really like this operating system, and im currently dual booting with vista of which i really don't like or use but i doubt such a problem would happened while using windows. When this happened it really surprised me and took me by surprised because i never encounter something like this when i was using windows as a main os. When I do the scan of my home folder it still says 100% used, but when I look at the break down, theres really nothing there. Ive even check within the hidden files, and still nothing is really there to take up space. Ive cleaned out the trash folder and everything. when i look at systems monitor it gives me a different reading, it say that since deleting the whole video folder i had that theres about 5 gigs left. anyhow, i must say thank you guys for great speed help. the forums are a great asset to ubuntu, i just cant wait till i learn more myself and contribute to help someone.

---

