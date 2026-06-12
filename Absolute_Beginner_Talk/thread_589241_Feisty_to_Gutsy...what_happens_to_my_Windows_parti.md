---
title: "Feisty to Gutsy...what happens to my Windows partitions?"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by biomedtech on 2007-10-24
I had a lot of help getting my Windows partitions to be recognized in Feisty Fawn.  If I go with a clean install of Gutsy, what is the chance they will stay recognized?  Is NTFS Tool upgraded in Gutsy, because I'm really concerned about losing access to my multiple Window's volumes. Thank you.

---

### Post by Bakon Jarser on 2007-10-24
I did a clean install and it mounted my ntfs windows partitions automatically with read/write capability.  Feisty only gave me read capability.  I'm not an expert though, just my experience.  It might help others to know if you have ide or sata drives.

---

### Post by edwardTheGreat on 2007-10-24
In my experience it recognises them fine (read-write) without any configuration, I have done a clean install on my laptop and an upgrade on my PC, and had no troubles with either as far as losing access to my NTFS partitions.

---

### Post by Maestro23 on 2007-10-24
I didn't have a problem after a clean install.  Just had to install ntfs-config.  After that, everything was golden.

---

### Post by Sef on 2007-10-24
> I had a lot of help getting my Windows partitions to be recognized in Feisty Fawn. If I go with a clean install of Gutsy, what is the chance they will stay recognized? Is NTFS Tool upgraded in Gutsy, because I'm really concerned about losing access to my multiple Window's volumes. Thank you.

**Back up** your data first.   It should recognize your partitions.  The NTFS tool is installed by default.

---

### Post by biomedtech on 2007-10-25
Thank you for all your suggestions. I'm downloading the iso file in order to go with clean install. I have copied my docs folder over to my XP volume, so even if something goes bad I can merely boot into Windows to retrieve. 

One thing that happened with Feisty, is that my XP "C" drive took a long time
to start up after Ubuntu was done with configuring everything. It sort of worked itself out, but for a short time I thought Linux had hosed XP.

---

