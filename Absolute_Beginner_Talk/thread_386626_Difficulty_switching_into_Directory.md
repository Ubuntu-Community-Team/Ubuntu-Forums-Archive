---
title: "Difficulty switching into Directory"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by splendid on 2007-03-17
I am logged in as a user in terminal mode.  There is a directory in my home directory that I am trying to access.  I can access it through File Browser or Nautilus, but not in terminal window.  Get message:

-su: cd: DVD: No such file or directory

What am I doing wrong?

---

### Post by eljalill on 2007-03-17
What code exactly are you using when you try to access the directory?

---

### Post by splendid on 2007-03-17
cd DVD Shrink

---

### Post by mcduck on 2007-03-17
The problem is the space in the directory name. You need to use either cd "DVD Shrink" or cd DVD\ Shrink.

Anyway, the easy trick is to just type cd DVD and then press TAB to automatically complete the name.

---

### Post by eljalill on 2007-03-17
What happens if you type
cd DV and then hit the tab-key ? It should autocomplete the name then .

If the name of the directory is: "DVD Shrink", you might have to type 
cd DVD\ Shrink  because of the space

---

### Post by splendid on 2007-03-17
Thanks to both of you.  The Tab key did the auto fill and that worked out great.  I appreciate your help.  Any recommendations on a DVD burner program, and one that is easy to install?

---

### Post by mcduck on 2007-03-17
> **splendid said:**
> Thanks to both of you.  The Tab key did the auto fill and that worked out great.  I appreciate your help.  Any recommendations on a DVD burner program, and one that is easy to install?
I usually use GnomeBaker for CD/DVD burning. Other option is K3B, both can be installed with Add/Remove, Synaptic or apt-get.

---

