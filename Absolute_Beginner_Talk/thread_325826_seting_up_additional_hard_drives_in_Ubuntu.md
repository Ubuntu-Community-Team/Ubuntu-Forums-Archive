---
title: "seting up additional hard drives in Ubuntu"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by rjprice on 2006-12-26
I need some help setting up extra hard drives using Ubuntu. 
this is my first time using this type of system and any help would be deeply appreciated.
TIA
ron

---

### Post by steve.horsley on 2006-12-26
What exactly are you trying to do? Are they existing drives or are you adding new drives? Are they new empty drives, or used with data on them? The more info you can giove the better.

---

### Post by lyceum on 2006-12-26
Also, have you tried to attach them yet, and were they recognized at all?

---

### Post by rjprice on 2006-12-26
I have 6 additional hd with graphics and music on them and Ubuntu does not see them. They all worked with xp pro. I put Ubunto on a new 40 gig hd and all seems to work ok cept seeing the hd's..

---

### Post by steve.horsley on 2006-12-26
Can you post the contents of the file /etc/fstab and the output of the command:
**sudo fdisk -l**
(that's a lowe-case L for list).

---

### Post by lyceum on 2006-12-26
How are they formated? Fat32 for example.

---

### Post by rjprice on 2006-12-26
they are NTFS for xp

---

### Post by rjprice on 2006-12-26
no access at all

---

### Post by lyceum on 2006-12-26
> **rjprice said:**
> they are NTFS for xp

Hmmm:-k 

The last time I tried working with NTFS I have to remove my data and reformat the drives. Later I learned that I did not have the master/slave jumper in the right spot. Are these internal drives, or external? My external reads then as read only files. Trying to help, but this might get beyond my knowledge, but my post will bump you back up to the top. I am going to look for something and be right back...


-edit-

[http://www.helpwithpcs.com/upgrading/install-hard-drive.htm](http://www.helpwithpcs.com/upgrading/install-hard-drive.htm)

If it is internal, this link might help, let me know.

---

### Post by rjprice on 2006-12-26
My son has a computer shop but he does not know the linux systems. all the hd's did work ok with xp. thea are all internal and are from 20--120 gig. If I take and put the original xp drive back into the system without Ubuntu all are readable.

---

### Post by OldTimeTech on 2006-12-26
Check this link out...it might help

[http://www.smorgasbord.net/book/export/html/195](http://www.smorgasbord.net/book/export/html/195)

---

### Post by esaym on 2006-12-26
Yes you will have to add all the drives into etc/fstab in the proper format

---

### Post by rjprice on 2006-12-26
am not sure how that is done..like i said before i am new to ubuntu

---

### Post by lyceum on 2006-12-27
Well, the easy way would be to get all of the useful info off the drives and re-format them. You can do this on Windows with a partitioner like partition magic, or you can use the live disk and put Ubuntu on them. They should be detected with the FAT32 setup. Once they can be recognized Ubuntu can format them. I am sure there is a way to look for them with Ubuntu and them reformat them, but I don't know what it is off the top of my head, but this post should bump you up again while I try to find it.

---

### Post by ron999 on 2006-12-27
Yes, I agree

Ubuntu can't see NTFS system files.
If you reformat those drives FAT32 they can then be accessed by both XP and Ubuntu.

---

### Post by lyceum on 2006-12-27
Well if you are feeling risky, try this:

[http://doc.gwos.org/index.php/NTFS-3g](http://doc.gwos.org/index.php/NTFS-3g)

but I am still looking... (and hoping someone smarter than me finds this tread)

-edit-

found this:

[http://wiki.linuxquestions.org/wiki/Add_a_new_hard_drive](http://wiki.linuxquestions.org/wiki/Add_a_new_hard_drive)

And felt dumb, as I use fdisk all the time (or use to anyway) but it look pretty good. Post is this does not help!

---

