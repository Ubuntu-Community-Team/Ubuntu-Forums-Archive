---
title: "Partitions on instalation"
date: 2005-09-03
forum: Absolute Beginner Talk
---

### Post by jc87 on 2005-09-03
I´m gonna to install ubuntu in my pc in a few days  ( this after an whole year planning my OS transition , with a lot of reading documents about gnu/linux , and playing with live-cd´s ).

I already i´ve read and re-read a couple of tutorials about the subject but i´m still with some doubt´s about instalation :

1)I have a NTFS partition that i do not want to keep , can i delect it using ubuntu or i need to insert wintendo XP cd´s for a last time?

2)I know that i will need at least a / partition ( equivalent to C: ) , and a swap partition with recomended size of 1,5 times my ram memory , but i can also have a bootable partition /boot ( if i dont want / to be te bootale partition) , and a /home partition .

There are any advantanges in having thoose two last partitions that i´ve mentioned ?

I´ve posted this question on this section because it looked like the most adquable place for it , if the moderators think that makes more sense in other place of the forum feel free to move it.

P.S.  Death do Wintendo and Microevil ( sorry couldn´t resist :roll: ).

---

### Post by TristanMike on 2005-09-03
[QUOTE=jc87]I´m gonna to install ubuntu in my pc in a few days  ( this after an whole year planning my OS transition , with a lot of reading documents about gnu/linux , and playing with live-cd´s ).[/QUOTE]Welcome to Ubuntu.[QUOTE=jc87]I already i´ve read and re-read a couple of tutorials about the subject but i´m still with some doubt´s about instalation :

1)I have a NTFS partition that i do not want to keep , can i delect it using ubuntu or i need to insert wintendo XP cd´s for a last time?[/QUOTE]Yes, absolutely, you will be able to wipe any and all existing partitions with the installer. You can check out the installation and partitioner here [http://mrbass.org/linux/ubuntu/install/](http://mrbass.org/linux/ubuntu/install/) and here [http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)[QUOTE=jc87]I know that i will need at least a / partition ( equivalent to C: ) , and a swap partition with recomended size of 1,5 times my ram memory , but i can also have a bootable partition /boot ( if i dont want / to be te bootale partition) , and a /home partition .[/QUOTE]The installer will create everything automatically if you choose to let it do this. I did and am running fine. As for the swap, I have 1GB or RAM and I have 768MB of swap, and I don't believe I've ever touched swap. The swap can be up to 2GB but this may be overkill, kinda depends on your specs and needs.[QUOTE=jc87]There are any advantanges in having thoose two last partitions that i´ve mentioned ?[/QUOTE]You need them?  :? Your /boot folder just contains the boot info and your home folder is where all of the users are stored, this is where most of your personal data will be kept ie. /home/<USER1> and /home/<USER2>.  Sorry if this isn't clear, but hope it helps.

---

### Post by aysiu on 2005-09-03
[QUOTE=jc87]
2)I know that i will need at least a / partition ( equivalent to C: ) , and a swap partition with recomended size of 1,5 times my ram memory , but i can also have a bootable partition /boot ( if i dont want / to be te bootale partition) , and a /home partition .

There are any advantanges in having thoose two last partitions that i´ve mentioned ?[/QUOTE] I'm not sure about the reasoning behind the separate /boot partition, but sometimes people make separate /home partitions to make upgrading or trying new distros easier. The /home folder is where all of your settings and preferences are (the look of your desktop, your browser's bookmarks, your emails, etc.), as well as where all of your files live (pictures, documents, music, etc.). So, if you ever choose to install a new distro or install a newer version of Ubuntu, you can just install it and leave your /home partition untouched.

That said, it is possible to just upgrade to the newest Ubuntu version without reinstalling it completely, but some people just like a "clean" install.

---

### Post by jameswilhelm on 2005-09-03
I have mostly used one partition for everything without a problem. Now I have my /home directory on a large disk and the rest on a smaller disk.

With a separate /home partition, presumably you'll do a new install or upgrade, and then later on mount the /home partition on the /home directory? What about programs that have not been able to add or update their config information in your home directory? 

Or do you specify the home partition at install/upgrade time and tell the installer to not format it?

---

### Post by aysiu on 2005-09-03
[QUOTE=jameswilhelm]
Or do you specify the home partition at install/upgrade time and tell the installer to not format it?[/QUOTE] Yes. This is what happens if you have a separate /home partition. Personally, I don't have a separate /home partition. I just save my .mozilla and .mozilla-thunderbird folders.

---

### Post by jameswilhelm on 2005-09-03
Thanks.

For Breezy, I will bite the bullet and just do an upgrade (after backing everything up, of course)!

---

