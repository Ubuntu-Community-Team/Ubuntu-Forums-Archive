---
title: "how do u edit source list"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by windows hater on 2007-05-29
what is the command to edit source.list

---

### Post by Inxsible on 2007-05-29
```
 gksudo gedit /etc/apt/sources.list
```
 
Make changes and save

---

### Post by aleksanderffs on 2007-05-29
sudo gedit /etc/apt/sources.list

---

### Post by Toxicity999 on 2007-05-29
Just tyr not to be too willing to add any repo you find to it, it could cause stability or even security problems later on. And NICE avatar =]

---

### Post by El_Quintron on 2007-06-13
Here's another question...

How do you save it? 

I did sudo nano /etc/apt/sources.list

but when I added the repository I didn't let me save...

does it auto save?

---

### Post by Inxsible on 2007-06-13
If you use gedit, you can hit ctrl+s to save or click the save icon. Or File --> Save.
 
I dont quite rbr how to save if you use nano. I hardly ever use nano. Is there a reason for you to use nano only?

---

### Post by Outrunner on 2007-06-13
> **El_Quintron said:**
> Here's another question...

How do you save it? 

I did sudo nano /etc/apt/sources.list

but when I added the repository I didn't let me save...

does it auto save?

In nano you have to press CTRL-X

---

### Post by Nekiruhs on 2007-06-13
> **aleksanderffs said:**
> sudo gedit /etc/apt/sources.list
Please dont use sudo gedit. I lost permissions in my sudoers file, and had to fix it. Not fun. please just be safe and use gksudo

---

### Post by El_Quintron on 2007-06-13
> **Inxsible said:**
> If you use gedit, you can hit ctrl+s to save or click the save icon. Or File --> Save.
 
I dont quite rbr how to save if you use nano. I hardly ever use nano. Is there a reason for you to use nano only?


Here's what weird, whenever I use GEDIT it doesn't let me save, (is it because I'm not logged into the gui as root? and if so how to I access the GUI as root?)

The save is always greyed out.

I used Nano because it was an instruction I got from the help files, to keep my wireless card firmware updated...

I'm ok at figuring stuff out but the language is so new to me that I flailing about most of the time

---

### Post by El_Quintron on 2007-06-13
Ok I've got it figured out I think:

All of the editing of sources has to be done in terminal and not in the text files within the gui I would assume?

I've bookmarked this thread and I'm going to do more of it at home and I'll have more questions later I think, but for now this should keep my explorations going.

I don't have any relevant data on this machine so it doesn't matter if I get some meltdowns/kernel panics overlaps.

I backed up all the data and I'm using it exclusively to learn linux so it's fine for the time being.

---

### Post by Inxsible on 2007-06-13
if you use sudo before gedit then you will be able to save.

---

