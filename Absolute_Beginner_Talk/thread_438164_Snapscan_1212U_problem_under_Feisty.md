---
title: "Snapscan 1212U problem under Feisty"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by spenny on 2007-05-09
Under Edgy I was able to scan using my Agfa Snapscan 1212U scanner and XSane.

Since the upgrade to Feisty, however, I can obtain a preview of what's on the scanner bed, but when I go to "Scan" the image I get a "Failed to start scanner: Error during device I/O".

Does anyone have any idea on how to fix this, what the cause could be?

Apologies if this is posted in the wrong forum.

Thanks in advance,
Andrew.

---

### Post by spenny on 2007-05-09
In case it's of any help, after the preview, when the scanning light bar (I don't know the technical term, I'm sorry) is returning to its original position, it stops about a third of the way back.

---

### Post by fsando on 2007-05-10
Hi spenny
Have you searched the forum? 
Anyway, you are out of luck for some time to come. See this thread (and many others):
[http://ubuntuforums.org/showthread.php?t=414474](http://ubuntuforums.org/showthread.php?t=414474)

Unfortunately no one who is in a position to do something about it seems to take this issue particularly seriously :(

It's probably of little help but at least your problem is acknowledged and will be not be dealt with immediately.

---

### Post by ewlabonte on 2007-05-11
I had the same problem with my snapscan under feisty. And the above link doesn't address the problem at all. It's not my hardware because it is the same problem with every computer that I have feisty installed on but the scanner works with other distros.

---

### Post by spenny on 2007-05-12
Thanks. The linked thread does make some mention of the problem, but it would seem to be a kernel problem, and one that they're not sure about fixing! :-(

There is a fix, but I'm not sure I want to tinker this much.

[http://ubuntuforums.org/showthread.php?t=432130](http://ubuntuforums.org/showthread.php?t=432130)

---

### Post by matala on 2007-06-04
Whith my Snapscan 1212u and Feisty I have solved the problem with:
"scanbuttond -r 1000000"
I have add this string in System/Preferences/Sessions, now my scanner works correctly.

---

### Post by ElrohirMacBeorn on 2007-09-08
> **matala said:**
> Whith my Snapscan 1212u and Feisty I have solved the problem with:
"scanbuttond -r 1000000"
I have add this string in System/Preferences/Sessions, now my scanner works correctly.

Hi 
Thanks a lot! Did work for me, too! Really saved my day!

Elrohir

---

### Post by lazork on 2007-10-19
> **matala said:**
> Whith my Snapscan 1212u and Feisty I have solved the problem with:
"scanbuttond -r 1000000"
I have add this string in System/Preferences/Sessions, now my scanner works correctly.

Thanks man!
I've been looking for a solution to this problem for months!!

Btw, I have an Acer 620u, but both the problem and the solution are the same

---

### Post by ColJep on 2007-10-29
Excuse my ignorance but could someone give details of how to add the string and where?
It sounds good as I cannot get my Snapscan 1212U working under Fiesty or Gutsy.

ColJep

---

