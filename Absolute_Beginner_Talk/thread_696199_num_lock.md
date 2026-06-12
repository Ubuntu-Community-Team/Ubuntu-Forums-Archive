---
title: "num lock"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by firewick on 2008-02-13
Hello, I was wondering if there was a file I could configure to have the num lock on for start up? I am using Ubuntu 7.10 and could not find any info on it after about 30 min of searching help files and forums... I appreciate any help.

Thanks,

Eric

---

### Post by jaytek13 on 2008-02-13
Here's a real quick and dirty tutorial for having numlock enabled at startup. 

[https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)

---

### Post by jpeddicord on 2008-02-13
If jaytek13's suggestion doesn't work, it may be related to your computer's BIOS. For instance, I know that on Dell systems you have to mash F2 on startup to get to the menu, and then look for a NumLock option. It's usually somewhere in there. If you can't find it, just reboot and avoid touching any other settings. :)

---

### Post by firewick on 2008-02-13
Thanks! Worked like a charm. It seems as though you came across it very quickly... Did you just search on it, or did you know the information was right there, if you don't mind me asking?
Thanks again,

Eric

> **jaytek13 said:**
> Here's a real quick and dirty tutorial for having numlock enabled at startup. 

[https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)

---

### Post by jaytek13 on 2008-02-13
> **firewick said:**
> Thanks! Worked like a charm. It seems as though you came across it very quickly... Did you just search on it, or did you know the information was right there, if you don't mind me asking?
Thanks again,

Eric

Google search for "numlock ubuntu" brought it up as the first result.

---

### Post by firewick on 2008-02-13
That it does... That's the last time I go straight to the forums to search! That just sold me on google. It wasn't even the fact that I put a space in it, google brings it up 1st either way.

> **jaytek13 said:**
> Google search for "numlock ubuntu" brought it up as the first result.

---

### Post by Feivel on 2008-03-08
> **jaytek13 said:**
> Here's a real quick and dirty tutorial for having numlock enabled at startup. 

[https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)

Will this work on Hardy Heron?

---

### Post by docusn on 2008-03-10
jaytek13 - thanx for the info.

When I try to save the file I get the error message 
 Could not save the file /etc/gdm/Init/Default./

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

I am a REAL noobie - so please have mercy and explain what I am doing wrong.

---

### Post by p_quarles on 2008-03-10
> **docusn said:**
> jaytek13 - thanx for the info.

When I try to save the file I get the error message 
 Could not save the file /etc/gdm/Init/Default./

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

I am a REAL noobie - so please have mercy and explain what I am doing wrong.
You need root permissions to edit that file. From a terminal:
```
gksudo gedit /etc/gdm/Init/Default
```
Make the changes, save the file, and you're set.

---

### Post by docusn on 2008-03-10
Thanks !

---

