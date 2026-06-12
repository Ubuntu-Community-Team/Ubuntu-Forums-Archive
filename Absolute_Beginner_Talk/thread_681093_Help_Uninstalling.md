---
title: "Help Uninstalling"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by samtboy1234 on 2008-01-28
Okay before i go on about my problem i just want to apologise for not sticking with ubuntu, im impressed that free software is available such as ubuntu but guys its not for me, right here i go

Ive searched hi and lo trying to find away of sorting this problem out but ive been unsuccessful every where. I have the latest version of Ubuntu currently installed on my laptop. I did this about one month ago. Stupidly i just installed it straight away so my computer has no partitions on it, its just installed on my hard drive. Its a decent piece of software, but things like youtube and ahem *coughs* xtube *shock* wont work due to codecs or whatever they are blah de blah, so basically i want to remove ubuntu and just put windows xp on the laptop.

Ive tried to install the cd from boot up but it doesnt recognise the hardrive or something? So i come to you for your advice, but im not very computer knowledgable so i would really appreciate it if someone could give me step by step instructions in baby language lol, im desperate for xp to come back, PLEASE HELP!!!!
:(:(:(:(:(

---

### Post by macogw on 2008-01-28
There are partitions on the hard drive.  Ubuntu set them up to begin with as one big one and then a little one for swap.  The problem you're encountering is most likely that Windows, being stupid, doesn't recognize very many filesystems and is confused because your hard drive is formatted as ext3.  If you boot from an Ubuntu live cd and use GParted (System -> Administration -> GNOME Partition Editor), you can delete the partitions and format it as FAT32 or NTFS.

As for YouTube, you just need Flash. install this:  [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

---

### Post by Cypher on 2008-01-28
If you have the WinXP installation CD (not restore CD) then you should be able to pop it in, have it delete everything on your HD and install Windows for you.

Does your HD work in Ubuntu right now? It's just a regular IDE drive so there should be no reason for the XP installation CD not to find your HD.

---

### Post by samtboy1234 on 2008-01-28
Thanks for the replies, no it just doesnt recognise it when i try to install it. So what to do next....? I have that gpart thing alreasy installed, sorry to be really blonde but im no good at these things.....:(:confused:

---

### Post by jan quark on 2008-01-28
if you have time, perhaps after you solve this out, or perhaps even now
here is a list of guides how to partition in Ubuntu
[http://janquark.fatfreehost.com/partitions.html](http://janquark.fatfreehost.com/partitions.html)

---

### Post by samtboy1234 on 2008-01-28
anyone there?

---

