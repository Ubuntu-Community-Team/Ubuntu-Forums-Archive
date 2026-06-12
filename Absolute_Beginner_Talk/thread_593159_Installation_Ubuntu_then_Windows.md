---
title: "Installation: Ubuntu then Windows"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-10-26
I'm thinking of installing Windows later on down the road.... How hard would it be to do
a duel boot in reverse order, that is, installing Ubuntu 1st then in a few months or
so when I have some extra time setting up Windows.  How much harder is it to
make this work?

---

### Post by taurus on 2007-10-26
If you install Windows after Ubuntu, you can only boot Windows since it will overwrite GRUB from MBR.  Therefore, you need to reinstall GRUB again so you can boot both Ubuntu and Windows.

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

### Post by devosion on 2007-10-26
Im assuming it shouldnt be all that hard. Just use the partition editor in Ubuntu before hand to setup NTFS somewhere on your drive. Insert the windows cd and install on that drive, and GRUB should give you the option of which OS to load upon start up.

---

### Post by Threbus5 on 2007-10-27
Let me see if I understand.
You want to install Windows?

Just joking.

Anyway.
This is an inelegant solution but may work.
1. Tar backup your Ubuntu.
2. Install Windows.
3. Install Ubuntu and choose to make it dual boot with Windows.
4. Tar the backup that you made into the partition that you installed Ubuntu after the Windows install.

Take care.

---

### Post by genbuntu on 2007-10-27
> **Threbus5 said:**
> Let me see if I understand.
You want to install Windows?

Just joking.

Anyway.
This is an inelegant solution but may work.
1. Tar backup your Ubuntu.
2. Install Windows.
3. Install Ubuntu and choose to make it dual boot with Windows.
4. Tar the backup that you made into the partition that you installed Ubuntu after the Windows install.

Take care.

ahh.. just stmbled upon this..
Can you explain me why to 'Tar' backup? any specific advantage?

Edit: sorry if it sounds stupid because I'm still learning.. :)

---

### Post by louieb on 2007-10-27
> **genbuntu said:**
> ...
Can you explain me why to 'Tar' backup? any specific advantage?...

There are two types of backup that I use. One is a partition backup with **partimage**. This is non-selective backup of a whole partition. I use this when making major changes such as upgrading from 7.04 to 7.10. The advantage over tar - its faster. Disadvantage should be run from a Live CD. 

The other is a **tar** backup. **tar** allows you to be selective about what to backup and or restore.  Advantage: selective restore, can be run on a live system. 

For more info go to the **How to section** of the forum and do a search. There a several good threads on using both.

---

### Post by bara_ac on 2007-10-27
uhm! hi!
I`m new to ubuntu... and I have, kinda, the same problem as one in this thread...
I had windows then I installed ubuntu. No problem booting. Then, I formatted the windows. Afterwards came the problem: it only boots in windows. I installed OSL 2000 and selected linux on the booting screen, but no answer for at least 30 minutes.
That`s the problem, and didn`t wanted to start a new thread.

---

### Post by sneezymelon on 2007-10-27
> **Threbus5 said:**
> Let me see if I understand.
You want to install Windows?

Just joking.

Anyway.
This is an inelegant solution but may work.
1. Tar backup your Ubuntu.
2. Install Windows.
3. Install Ubuntu and choose to make it dual boot with Windows.
4. Tar the backup that you made into the partition that you installed Ubuntu after the Windows install.

Take care.

Why not rather kill yourself??

Install Windows and then restore the grub using the LiveCD...It's as simple as that

---

### Post by Orbital75 on 2007-10-27
Humm.... Well, I may just bite the bullet and install Windows first then Ubuntu but
since windows needs reinstalling constantly ( Let's say yearly ) wouldn't I eventually
run into this problem and have to install windows with Ubuntu already working
correctly?

---

### Post by taurus on 2007-10-27
> **Orbital75 said:**
> Humm.... Well, I may just bite the bullet and install Windows first then Ubuntu but
since windows needs reinstalling constantly ( Let's say yearly ) wouldn't I eventually
run into this problem and have to install windows with Ubuntu already working
correctly?

Look at the link in my #2 post!

---

### Post by Orbital75 on 2007-10-27
Thanks....

---

### Post by genbuntu on 2007-10-28
> **louieb said:**
> There are two types of backup that I use. One is a partition backup with **partimage**. This is non-selective backup of a whole partition. I use this when making major changes such as upgrading from 7.04 to 7.10. The advantage over tar - its faster. Disadvantage should be run from a Live CD. 

The other is a **tar** backup. **tar** allows you to be selective about what to backup and or restore.  Advantage: selective restore, can be run on a live system. 

For more info go to the **How to section** of the forum and do a search. There a several good threads on using both.

thank you loueib.

---

### Post by erginemr on 2007-10-28
You may install Windows on top of Ubuntu, but will lose the grub settings in MBR (master boot record) because Windows will overwrite the MBR blindfold with its own settings. 

Fortunately, there are ways to restore Grub later on using Ubuntu Live CD and our beloved  forum packs lots of information on that. The following thread will help you out in such a case:
[http://ubuntuforums.org/showthread.php?p=1308395](http://ubuntuforums.org/showthread.php?p=1308395)

---

