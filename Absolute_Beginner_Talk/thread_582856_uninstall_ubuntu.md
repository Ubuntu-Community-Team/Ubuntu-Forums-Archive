---
title: "uninstall ubuntu"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Narv on 2007-10-20
Hi, hopefully this is straight forward to resolve, as I created the problem easily enough!

I wanted to upgrade feisty on my laptop to gutsy, but my laptop doesn't have an internet connection.  It installed fine from CD, but instead of upgrading I have ended up with two separate ubuntus and its really slow!  Stupid really, but how can I go about deleting one of them?  

Ive already made a copy of the files I want to keep from feisty.

Thanks

---

### Post by tzulberti on 2007-10-20
You can format the Feisty partition and then update the grub menu.

---

### Post by Narv on 2007-10-20
Thanks for responding, but I'm not sure what that means.  How do I format it? And where is the grub menu?

---

### Post by tzulberti on 2007-10-20
I was wrong with editing the grub menu. There is an option in windows to restore the MBR, that is where one generally installs the grub. I can't remember how to do that (look in google, there should be info abuout it).
Formatting isn't the word here. I should say to delete the partition where Ubuntu is installed.

---

### Post by spyker3292 on 2007-10-20
You could burn a copy of GParted and just boot from it and delete the extra partition.

---

### Post by Duck2006 on 2007-10-20
You can use gparted to delete your unwanted partition and resize or make new one.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

