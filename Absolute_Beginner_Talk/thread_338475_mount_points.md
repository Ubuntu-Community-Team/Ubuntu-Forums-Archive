---
title: "mount points"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by salted-tator-tot on 2007-01-14
I have just setup my partitions and gave the new one (ext3) 11 GiB of space, I clicked next and it gave me two columns. Both offer the same choices but I wasn't sure what to pick. It says Mount Point and under that are two drop-down boxes letting me choose from:

(blank), swap, /, /home, /boot, /usr, /var

then after that it gives the space (11 GB) and then another drop-down menu offering two choices which are:

Partition 1 and Partition 2 (Partition 2 is the ext3 partition)

And then the same under it (2 columns in all). So what do I do now?

---

### Post by salted-tator-tot on 2007-01-14
I just googled and I'm not sure if this is right for what I'm doing but it said to make one column blank and the other swap and the swap one check the reformat. Is this correct?

---

### Post by Pobega on 2007-01-14
I don't understand your question; What are you trying to do, and what program are you using?

---

### Post by salted-tator-tot on 2007-01-14
I just setup my partition for ubuntu and now I want to know what do I do next? I am on the page that says: Prepare Mount Points. So what do I do?

---

### Post by salted-tator-tot on 2007-01-14
should I have more than one partition for ubuntu? Or is one ext3 partition all that is needed?

---

### Post by logos34 on 2007-01-14
> Partition 1 and Partition 2 (Partition 2 is the ext3 partition)

If all you have is a root and swap then things should look like this:

Mount Point            Size                         Partition                                       Reformat? 
swap                                    Partition 1 Disc IDE/ATA 1 (Primary) (hda1)                 X                               
/                                          Partition 2 Disc IDE/ATA 1 (Primary) (hda2)           X

click forward

[edit: can't get spacing right!]

---

### Post by salted-tator-tot on 2007-01-14
Sorry for the now triple, but after resizing it to 11, should I just go back and click use remaining free space (or whatever it is)

---

### Post by logos34 on 2007-01-14
you need swap AND ext3 / root.

---

### Post by salted-tator-tot on 2007-01-14
So can I just go back and click "use remaining space" after deleting the partition I just made (the ext3)

---

### Post by logos34 on 2007-01-14
have a look [here]("http://psychocats.net/ubuntu/installing")

---

### Post by salted-tator-tot on 2007-01-14
Its done loading and nothing is coming up.

---

### Post by salted-tator-tot on 2007-01-14
nevermind, I just refreshed it and its working.

---

### Post by salted-tator-tot on 2007-01-14
I just clicked "use largest continuous free space" and it is installing.

---

