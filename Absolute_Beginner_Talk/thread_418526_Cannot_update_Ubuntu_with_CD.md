---
title: "Cannot update Ubuntu with CD"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-04-22
Hello, I'm trying to update Ubuntu 6.10 to 7.04 with Install CD. I just downloaded it on my office computer, checked MD5, burned as iso image, tried on my office computer and it started automatically. But when I insert it in my Laptop, where I have ubuntu 6.10, it doesn't start automatically, but opens as a window containing folders instead. 

also, the alternetive offered by help site doesn't do anything:

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

gksu "sh /cdrom/cdromupgrade" 

while restarting computer, it autimatically works as a boot cd, so I don't understand what problem there should be..

what shoud I do?


It's too late now, noone replied and I reinstalled the root partition totally. Now, the problem is that I had my home directory and shared data as another partition and while installing, it created another home folder on the same partition where "/" is, so somehow ignored old home folder. How can I switch it now to the old home folder?

---

### Post by zvacet on 2007-04-22
To upgrade from Cd you need alternate CD,as you can read in how to upgrade page.

---

