---
title: "Accessing /home from another partition?"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-04-06
I am currently moving my /home to a new partition using [aysiu's guide.]("http://www.psychocats.net/ubuntu/separatehome")

If moving my home partition doesn't make my computer run faster, I will reformat my OS partition. The question is, if I reformat my OS partition, can I still use the /home partition that I am making today?

Edit: I installed Ubuntu in a new partition. I want to access my /home from Ubuntu from another partition. How can I do that?

---

### Post by indytim on 2007-04-06
If I understand your posting correctly, when you re-install your ops, select the manual partition thinger.  While in there, just identify the correct partition for your /home.  This is exactly why it is sometimes beneficial to put your /home on a seperate partition.

Good Luck,

IndyTim

---

### Post by mac.ryan on 2007-04-06
Yes you can. There are two schools of thoughts on the forums:

[LIST=1]
[*]Just reinstall the OS and the applications... and they will even find back their settings (hidden files in /home).
[*]Move the hidden files in /home to a subdirectory, reinstall the OS and the applications, and then try to selectively bring back hidden files in their original positions.[/LIST]School-of-thought #1 is the most common, supporters of the option #2 state that if you follow option #1 the installer won't generate important information that are installation-dependent (thus the system might get instable at some point).

Anyhow: for what concerns your documents, you can be 100% sure you will be able to still access them, provided that you will recreate users with the same name/password and in the same order....

---

### Post by 67GTA on 2007-04-06
You can reuse it. What do you mean by faster? What is slow? Moving /home to a separate partition is not going to gain you much speed. You might want to look at applying some tweaks before you go through all of that trouble.

---

### Post by wersdaluv on 2007-04-06
I have a new problem.

I installed Ubuntu in a new partition. I want to access my /home from Ubuntu from another partition. How can I do that?

---

### Post by Dimebag999 on 2007-04-06
hrr - this took me ages

---

### Post by HeelsFan on 2007-04-06
If you didn't specify the home partition in the install process then I think you have to manually mount the drive as home.  First, figure out what the home partition is named and then you can just follow the instructions about half down in this link to mount the new partition as home (replace the drives with your home partition drive name).

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by mikewhatever on 2007-04-06
> **wersdaluv said:**
> I have a new problem.

I installed Ubuntu in a new partition. I want to access my /home from Ubuntu from another partition. How can I do that?

If home partition is properly mounted during Ubuntu reinstallation, there is no reason you should not be able to eccess it. It should be the same as accessing the old home folder, namely through Nautilus file browser.

PS: Why do you expect Ubuntu to run faster with separate home?

---

