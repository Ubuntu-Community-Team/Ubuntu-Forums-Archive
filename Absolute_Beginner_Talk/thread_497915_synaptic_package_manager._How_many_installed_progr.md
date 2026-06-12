---
title: "synaptic package manager. How many installed programs ?"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by halesquad on 2007-07-10
I am trying to make my system as light as possible and just wondered if the number of packages that are installed in the synaptics affects the performance of the computer. 

I have got 22214 packages listed, 1250 installed

That is what it says in the bottom of the screen on the synaptic package manager.

How do i make my system light?


Thanks 

Stephen

---

### Post by p_quarles on 2007-07-10
Are you trying to make it "light" in terms of memory, storage, or both? 

If you're concerned about memory, you should opt for a lighter desktop environment (such as Xfce). The number of packages installed has nothing to do with how much memory you're using. That is, unless you've set every single app on your system to load at startup.

If it's hard drive space you want to free up, just uninstall the apps you don't want. At the same time, if you see something and Synaptic, and you aren't sure what it is, it's probably a dependency for something else you use, and you shouldn't remove it. 

1250 packages is really not a lot. That's a pretty minimal installation, and most of those packages are taking up very little space on your drive.

---

### Post by KIAaze on 2007-07-10
Useful programs to free space:
-localepurge
-deborphan
-debfoster

To know which programs take the most space:
In Synaptic:
Select filter->installed packages on the left, then sort the list by size

Command-line:
> dpkg-query -W --showformat='${Installed-Size;10}\t${Package}\n' | sort -k1,1n

---

