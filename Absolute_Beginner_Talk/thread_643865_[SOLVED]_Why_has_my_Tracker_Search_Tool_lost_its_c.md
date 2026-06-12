---
title: "[SOLVED] Why has my Tracker Search Tool lost its categories -screenshot."
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-12-18
Tried uninstall and reinstall.

[solved] by reindexing.

---

### Post by Thelasko on 2007-12-18
I'm not familiar with this program.  However, I am willing to bet it's because of some changes to your /home directory.  Programs like to store their user data as a hidden file in there.  Go to your /home directory and press ctrl+h to view the hidden files and see if there is one called ".trackers search tool" or similar.

---

### Post by philinux on 2007-12-19
Sorry that did not help.

---

### Post by Thelasko on 2007-12-19
Can you post any more information?  What happened right before you had this problem?

---

### Post by philinux on 2007-12-19
Take a look at the screenshot. Post me what yours looks like.

What I did was untick enable indexing cos trackerd was hogging my system.

Thought i'd give it one more try and enabled it again. It would not index so removed and reinstalled.

Got that screenshot of search. Oh and it wont find anything. Tracker is busy indexing it's not finished but tracker-stats show this.
default : 0 
Files : 8878 
Folders : 1524 
Documents : 824 
Images : 1338 
Music : 12 
Videos : 9 
Text : 400 
Development : 1121 
Other : 3650 
Emails : 0 
EvolutionEmails : 0 
ThunderbirdEmails : 0 
KMailEmails : 0 
EmailAttachments : 0 
EvolutionAttachments : 0 
KMailAttachments : 0 
Conversations : 0 
GaimConversations : 0 
Applications : 365

---

### Post by Thelasko on 2007-12-19
I'm no expert on the program, but if it works like Google Desktop Search it takes quite a while to index.  

If it doesn't index you won't see anything.  If the indexing is hogging your system increase the delay for indexing so it won't interrupt your work as much.  Since you just reinstalled it I would let it index overnight and see what it does.

I'm on a windows machine right now and I don't know when I will have time to play with my Linux machine right now.  Sorry I couldn't be more of a help.

---

### Post by philinux on 2007-12-19
I'm getting some results from the search now but double clicking any does nothing.

It's indexed about 16,000 files I've got it set for maximum performance but according to TOP it's only using 4%cpu

---

### Post by philinux on 2007-12-20
Ok progress, it's indexed about 35000 files.

I now get categories but thats it. The right hand side pane is missing where the info should be.

 - see attached screenshot

---

