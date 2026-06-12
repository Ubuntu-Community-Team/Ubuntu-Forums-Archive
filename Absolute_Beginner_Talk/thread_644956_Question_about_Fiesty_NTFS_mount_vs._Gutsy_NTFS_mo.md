---
title: "Question about Fiesty NTFS mount vs. Gutsy NTFS mount"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by laptoplinux on 2007-12-19
In Feisty, I could always mount my Windows partition with read-only access whether the partition was hibernated or not.  In Gutsy, I get a mount error if I try to mount the Windows partition while it is hibernated, but it works fine if the Windows partition is shut down.  I guess this is a change in the driver used to handle NTFS support, and the new way does seem to allow write support in a shut down partition.  

Here are my questions:

1.)  How safe is the Gutsy write support on a shut down drive?  For the longest time I've heard that using Linux to write to an NTFS partition was either not possible or very dangerous.  I take it the issues have finally been cleared up?  Is it ok now?

2.) Is there anyway to change things in Gutsy so that I can mount a hibernated NTFS partition with read-only like before, but still get read-write on a shut down partition?  If not, that's ok.  I'll just have to get in the habit of shutting down Windows before booting Gutsy instead of using hibernation so much.

---

### Post by Inxsible on 2007-12-19
First of all, I don't know what you mean exactly by 'shut down drive'. If you mean you properly shut down Windows before logging into Linux, then that's the way you should do it.

You should NEVER hibernate one OS and then log into another using the same drives. This will create havoc with your drive and your data.

1) It is very very safe to write to NTFS partitions from a Linux environment

2) This is kinda moot, given my explanation above.

---

