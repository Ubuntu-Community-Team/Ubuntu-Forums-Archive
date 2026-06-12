---
title: "SoundCard problem"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by apparle on 2007-08-30
I have installed Ubuntu Fiesty Fawn 7.04 x86-64.
I have a intel dual core machine with foxconn RC4107MA-RS2 mother board
T hve ATI IXP SB450 south bridge and Realtek Sound card.
I have reffered to other posts and found out that there is a problem with alsa and it detects SB400 instead of SB450 . There was somthing about patching, which i didn't understand
I am new to linux though i have used Windows.
Plaese help.


**IMPORTANT** : I donot have internet connection and use net in my college

Another Problem : Whenever I extract any .tar.gz file i receive an error

---

### Post by Daveth on 2007-08-30
can you post the link to the instructions you are having problems with, and your tar.gz error- helps the folks here help you out.

---

### Post by apparle on 2007-08-31
[http://ubuntuforums.org/showthread.php?t=251123](http://ubuntuforums.org/showthread.php?t=251123)

This is the thread in the end there is a patch.
I am used to .exe patches in windows so sme help required here.



I could not understand you reply about your reply aout .tar.gz
Another thing i get htis problem in only amd64 version
The 32 bit version works fine

---

### Post by Daveth on 2007-08-31
um, kernel re-builds are beyond my skill to advise- someone else?

the end of your first post alludes to a .tar.gz file extraction problem !!!

---

### Post by apparle on 2007-09-07
Problem of .tar files solved
The problem was with filesystem
When i moved file from fat32 to ext3 it was fine

---

