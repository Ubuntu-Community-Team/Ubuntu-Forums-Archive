---
title: "[SOLVED] File Manipulation?"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by ramblinbill on 2008-03-08
What am I missing?  Why can't I drag a file from one directory/drive to another?  It goes with my curser, then snaps right back!  There's GOT to be a switch somewhere I haven't flipped.
I don't understand why you can't just drag, or right-click and send...

Sometimes my external drive is there, sometimes it's not...?

I love Ubuntu and am ready to leave Windows, but my head hurts.  Shouldn't basic file manipulation be just that?

Help would be appreciated...

Thanks

---

### Post by ODF on 2008-03-08
> **ramblinbill said:**
> What am I missing?  Why can't I drag a file from one directory/drive to another?  It goes with my curser, then snaps right back!  There's GOT to be a switch somewhere I haven't flipped.
I don't understand why you can't just drag, or right-click and send...

Sometimes my external drive is there, sometimes it's not...?

I love Ubuntu and am ready to leave Windows, but my head hurts.  Shouldn't basic file manipulation be just that?

Help would be appreciated...

Thanks

You can, except in the file system ... wich isn't true since you can run your file manager with sudo.

Sometime I use my explorer in my virtualbox as file manipulation ... since I like it.

---

### Post by halitech on 2008-03-08
if you are copying files within your home folder, no reason at all but if you are trying to go outside your home folder, that would be why. what are you trying to move and why?

---

### Post by ramblinbill on 2008-03-09
> **ODF said:**
> You can, except in the file system ... wich isn't true since you can run your file manager with sudo.

Sometime I use my explorer in my virtualbox as file manipulation ... since I like it.
I think I don't know what "sudo" is...guess I'm in for some reading...

---

### Post by ramblinbill on 2008-03-09
> **halitech said:**
> if you are copying files within your home folder, no reason at all but if you are trying to go outside your home folder, that would be why. what are you trying to move and why?
When I download music files, it puts them in "home"  I'm trying to move them over to an external drive where I store all that stuff

---

### Post by halitech on 2008-03-09
do you have the external drive mounted in your home folder? can you post your fstab file

```
gksu gedit /etc/fstab
```

---

### Post by ramblinbill on 2008-03-09
> **halitech said:**
> do you have the external drive mounted in your home folder? can you post your fstab file

```
gksu gedit /etc/fstab
```
How do I run these "codes" I see folks referring to?  Such as:

gksu gedit /etc/fstab

Where do I go to exedute them?

Thanks

---

### Post by absolution87 on 2008-03-09
hey,
to run codes you go to Applications->Accessories->Terminal

---

### Post by halitech on 2008-03-09
open a terminal - Applications - Accessories - Terminal and then paste the command in

---

### Post by ramblinbill on 2008-03-09
so, I go to the terminal and paste this command in?

---

### Post by absolution87 on 2008-03-09
yeah you can either paste or type but to save errors just paste it in

---

### Post by halitech on 2008-03-09
yes, it will open gedit, then copy and paste the info here

just don't make any changes yet till someone tells you. You are opening the file as root so you will be able to write to the file and if you make any wrong changes, it can mess your whole system

---

