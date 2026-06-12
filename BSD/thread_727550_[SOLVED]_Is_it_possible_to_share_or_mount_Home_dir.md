---
title: "[SOLVED] Is it possible to share or mount /Home directory in Ubuntu (ext3) as /Home i"
date: 2008-03-17
forum: BSD
---

### Post by the8thstar on 2008-03-17
Hello,

Is there a way to share my current Ubuntu /Home folder between Ubuntu 7.10, FreeBSD 7 and Solaris 10? The /Home folder is written on its own partition which is ext3 type. 

If it were possible, it would definitely motivate me to install FreeBSD and Solaris again on my hard drive. Thank you in advance for your help.

---

### Post by cammin on 2008-03-17
Find out what your version of BSD calls the /Home partition and add it to fstab. You may have to add it as an ext2 partition.

That's assuming it's on the disklabel somewhere. If it was detected, it's probably on G H or I
run disklabel and see if there's a linux partition that's the right size.
If not you'll have to add it.
Read up on disklabel and learn how to enter the correct info to one of the free partitions.

---

### Post by mips on 2008-03-18
I would not advise you to share /home between different operating systems or even different linux distros. It has implications which are not so nice.

---

### Post by Tomatz on 2008-03-18
Yeah you could but i suspect it could cause major problems unless you just shared directories in home (e.g. /home/bsd) and not your user directory.

---

### Post by the8thstar on 2008-03-29
Thanks guys.

After I realized the implications of this, I opted for something a little easier: just put a shorcut in the left panel in Gnome so that I can access my Home partition documents.

Harmless and very useful.

---

### Post by mips on 2008-03-29
> **the8thstar said:**
> Thanks guys.

After I realized the implications of this, I opted for something a little easier: just put a shorcut in the left panel in Gnome so that I can access my Home partition documents.

Harmless and very useful.

That is probably the better option.

---

### Post by Ptero-4 on 2008-04-02
Well. If you have different users, you can indeed share the /home folder. Each distro will only see the users it have set (since user account info is in a textfile in each distro's /etc), and you can put a public folder in /home and put your documents there.

---

### Post by Bachstelze on 2008-04-04
> **Ptero-4 said:**
> Well. If you have different users, you can indeed share the /home folder. Each distro will only see the users it have set (since user account info is in a textfile in each distro's /etc), and you can put a public folder in /home and put your documents there.

That's more or less what I do, too. In fact, I have a single /data partition that I use for all data storage. Then I have a folder in it where all my home dirs go (like /data/home/firas_ubuntu, /data/home/firas_gentoo, /data/home/firas_freebsd and so on). One thing to remember is that putting your home folder at /home/user is just a default choice, and you're defeinitely free to put it somewhere else if it suits your needs better.

---

### Post by the8thstar on 2008-04-13
I think I'll try this possibility if I install OpenSUSE or Gentoo or Fedora. I wouldn't try with FreeBSD 7.0, as I'm to scared of the results because of the different formats. And of course, I'm not going to try this with Vista as it just WOULDN'T work. :)

---

