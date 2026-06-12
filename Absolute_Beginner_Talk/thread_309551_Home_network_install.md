---
title: "Home network install"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by 8ball on 2006-11-29
Well, I think I'm ready to take the plunge.  I'm planning to download 6.06.

  I'd like to set up a home file server for several Win XP machines.  I have two questions (for now):

  Q1:  I see there is a "server install" option that apparently does not have a GUI.  I'm thinking that this would be a good way to kick-start me into working with a command-line again (haven't done that since the good old days of DOS).  Is this a good idea or am I being masochistic?  Would I be better off doing a "standard install"?

  Q2:  I have a hard drive full of files (NTFS) that I would like to use as my "data" drive for sharing.  I'm still a little confused about NTFS support.  Can I use this drive or will I have to re-format as FAT32 to be able to share files between the Win boxes?

  Thanks in advance.

---

### Post by freebeer on 2006-11-29
My take:

A GUI-based version doesn't take anything away from tinkering under the hood with command line.  In fact, you'll find yourself using the command line a lot if you're truly interested in learning the OS.  

From what I understand, an NTFS file system is best set up as a read-only partition in Linux/Ubuntu - writing to it can be problematic.  (I don't have first-hand experience on this - just what I've read on these forums.)  If you're fine with one-way sharing, then keep the NTFS partition.  If you really want two-way communication then FAT would be the way to go, I think.

---

### Post by wpshooter on 2006-11-29
> **8ball said:**
> Well, I think I'm ready to take the plunge.  I'm planning to download 6.06.

  I'd like to set up a home file server for several Win XP machines.  I have two questions (for now):

  Q1:  I see there is a "server install" option that apparently does not have a GUI.  I'm thinking that this would be a good way to kick-start me into working with a command-line again (haven't done that since the good old days of DOS).  Is this a good idea or am I being masochistic?  Would I be better off doing a "standard install"?

  Q2:  I have a hard drive full of files (NTFS) that I would like to use as my "data" drive for sharing.  I'm still a little confused about NTFS support.  Can I use this drive or will I have to re-format as FAT32 to be able to share files between the Win boxes?

  Thanks in advance.


8ball:

Unless you have a lot of experience with Linux, I think you are going to find that what experience you had with DOS in the past is going to be of very little help to you.

Install Ubuntu 6.06.1 from the DESKTOP CD, preferrably on a PC with NO other O/S on it and see what you are getting yourself into before you attempt something and mess your current Windows boxes up.

Good luck.

---

### Post by Josh1 on 2006-11-29
Or install the server then do:
```

sudo apt-get install ubuntu-desktop

```

Then you have server + ubuntu desktop :).

---

### Post by 8ball on 2006-11-30
Thank you all!  Based on your advice, I am going to:

1.  Install from the Desktop CD to my primary hard drive.

2.  Install the NTFS hard drive as a secondary drive. 

3.  Experiment and learn.

4.  Probably be back with more questions later. ;)    

Thanks again for getting me off to a good start.

---

