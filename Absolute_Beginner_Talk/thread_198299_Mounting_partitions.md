---
title: "Mounting partitions"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by learning on 2006-06-17
I know this is basic, but I have searched other threads and can't seem to find what I need.

I have four partitions:

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       21675    10241406   83  Linux
/dev/hda2           21676       43350    10241437+  83  Linux
/dev/hda3           43351       57800     6827625   83  Linux
/dev/hda4   *       57801       62118     2040255   82  Linux swap / Solaris
jason@jason-desktop:~$ gksudo nautilus

First is Ubuntu, Second is /home

The third partition is for another distro (FC5) I wanted to play with.

I can "see" it in nautilus but can't mount it. 

What do I need to do?

Thanks!

---

### Post by aysiu on 2006-06-17
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by learning on 2006-06-17
You are my hero, yet again!

Thank you!

---

### Post by sickenmcsluggets on 2006-06-17
This straightforward tutorial helped me immensely as well...thanks a lot, and I like your psychocats.net!

---

### Post by waldorf on 2006-06-25
[QUOTE=aysiu][http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)[/QUOTE]
I made a booboo.

I follow this guide while I was using FC5 on one partition on my laptop. The idea was that I was going to be able to access my files from my Ubuntu laptop and share back and forth. Needless to say that was a mistake and now I can't get into my home folder on Ubuntu.

How do I reverse what I did?

How do I get my permissions back to the old way.

---

### Post by aysiu on 2006-06-25
I don't know if you can get the permissions back to the old way. You can change ownership... you can probably change permissions on all of the files to a certain set... but not all files require the same permissions (some need to be 600; others need to be 644).

Honestly, your best bet is to rescue your important files and... reinstall.

---

### Post by waldorf on 2006-06-25
[QUOTE=aysiu]I don't know if you can get the permissions back to the old way. You can change ownership... you can probably change permissions on all of the files to a certain set... but not all files require the same permissions (some need to be 600; others need to be 644).

Honestly, your best bet is to rescue your important files and... reinstall.[/QUOTE]
Thanks for the response. I think you are right that a reinstall is the way to go.

---

