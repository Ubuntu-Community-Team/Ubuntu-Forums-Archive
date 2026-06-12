---
title: "rhythmbox"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by rlauderb on 2007-08-11
everytime i try to import music into rhythembox it tells me there is no storage space.  i know there is space because i've deleted like 40 songs.  does any one have any idea how to fix this?

---

### Post by eapache on 2007-08-11
Can you post the more precise error message?

---

### Post by rlauderb on 2007-08-11
error transferring track

no space left on the resource

---

### Post by eapache on 2007-08-11
Go into Applications>Accessories>Disk Usage and make sure that it says you have free space.

---

### Post by rlauderb on 2007-08-11
can't find applications

---

### Post by Nebby on 2007-08-11
It should be on the toolbar on the top edge of your screen. If it's not there, look for a button with the ubuntu logo on it (incase you're not sure what that is, it's the three people next to the ubuntu forums sign at the top left of this page)

---

### Post by p_quarles on 2007-08-11
Or, try this. Hit alt-F1 to bring up the command line, and then type:
```
df -h
```
and post the output here.

---

### Post by Clay Ferguson on 2007-11-25
I'm having the same problem.  I used your 'df -h' suggestion to determine that the iPod IS in face reporting it has NO space left.  But the gui (music player) shows NO FILES on the iPod.  It looks empty.  So the question is: What is eating up all the space on the iPod that cannot be seen by the music player.  Or: Why doesn't the music player show WHAT is eating up all the space???

---

### Post by Clay Ferguson on 2007-11-25
UPDATE - PROBLEM SOLVED: 

Here is how I solved the problem.  I opened the iPod in the "File Browser" (available via desktop icon) and looked for files eating up space.  Remember the 'dh -h' command can allow you to confirm this is the problme. In File Browser I found the iPod_Control/music folder had tons of files NOT being shown in the player.  Just sitting there eating up space. So I just deleted them using the File Explorer.  That cleanded up everything.  BTW: Normally you don't want to jack around with files in there manually however.  Use the Music Player to copy files to iPod! ;-)

Anyway now iPod works fine under UBUNTU!!!!  Yessss!

---

### Post by neurophyre on 2008-03-03
I'm also having this problem.  I've moved multiple files to trash in Rhythmbox from the iPod, ejected and reconnected it, but files are not actually being deleted.  They don't appear in Rhythmbox any more but they're still taking up space.

/dev/sdb2             7.5G  7.5G     0 100% /media/MY IPOD

This is a 1 generation older nano and Rhythmbox 0.11.2 on Gutsy.

---

### Post by neurophyre on 2008-03-03
I've filed a report.  Please see [http://bugzilla.gnome.org/show_bug.cgi?id=520044](http://bugzilla.gnome.org/show_bug.cgi?id=520044) 

As it stands now, a full iPod affected by this bug is currently read-only with Rhythmbox.

---

