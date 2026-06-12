---
title: "copy from an ntfs drive to a Linus drive?"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Vodkayum on 2007-06-24
How do I copy files from an NTFS formatted drive to a Linux formatted drive. I'm using Kubuntu 7.04 and when I try to set permissions it states that I do not have ownership of the drive. 

I tried sudo cp /source* /destination but I think an option is needed to fulfil this because it didn't work.\

anyone know how?

---

### Post by gn2 on 2007-06-24
Just cheat and use [www.getautomatix.com](www.getautomatix.com).

It has an NTFS auto-mounter which will automatically mount and make writeable any Fat32 or NTFS partitions or drives.
(Available in the "Miscellaneous" category once you've got Automatix installed)

As with all Linux software there's no guarantees of reliability.....

But it works flawlessly in my experience.

---

### Post by Vodkayum on 2007-06-24
Why did no one tell me about this before kickazz thanks a bunch.
I have google earth now too yay.

---

### Post by Vodkayum on 2007-06-24
seriously someone needs to sticky that app I have firefox now too.

GN2 You are my hero

---

### Post by Vodkayum on 2007-06-24
still need help, I can write to my ntfs drive now but my ext3 drive is still set to root only lol.
Getting close. That automatix software still owns though it gave me firefox and many other cool apps.

How do I get full access to my 90gigs of ext3 formatted drive?

---

### Post by gn2 on 2007-06-24
You would perhaps be better starting a new thread on that if you don't get it sorted, I haven't a clue how to manually change permissions from root to a user.

Hopefully someone who does will help.

---

