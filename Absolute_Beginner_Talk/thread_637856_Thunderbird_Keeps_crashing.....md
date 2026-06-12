---
title: "Thunderbird Keeps crashing...."
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by aj5string on 2007-12-11
As in the title really...

Start it, it downloads the messages, gets to the last one and crashes... I've got rid of some of the messages from the inbox that its d/loading from, but it always gets stuck on the last one...

haven't changed anything recently so i can't be that...

any ideas?

Alex.

---

### Post by philinux on 2007-12-11
First try 

File - compact folders.

---

### Post by aj5string on 2007-12-11
> **philinux said:**
> First try 

File - compact folders.

I tried, but I cant do that before it crashes tho!

---

### Post by philinux on 2007-12-11
open a terminal and type.

```
thunderbird -safe-mode
```

---

### Post by alienexplorers on 2007-12-11
Try deleting the localstore.rdf file in your profile folder.  Thunderbird will create a new one to replace the deleted one.  If that does not work try creating a new profile using:
> thunderbird -profilemanager

---

### Post by harold4 on 2007-12-11
1, Open thunderbird using "thunderbird -safe-mode" as stated above.  
2. Disable your addons. 
3. Start thunderbird normally.
4. Enable one at a time to figure out which is bombing.
5. repeat 3 and 4 as needed.

My guess is something blew up in lightning, assuming you have it installed.

---

