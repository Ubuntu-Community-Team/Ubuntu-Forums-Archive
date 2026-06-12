---
title: "Installed edgy lost MBR."
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by bchivers on 2007-02-19
Now I can't boot into windows.

---

### Post by tubasoldier on 2007-02-19
Well, for some reason it was not added to grub then.

```
sudo gedit /boot/grub/menu.lst
```

then at the bottom of that file add the following

```

title         Windows 95/98/NT/2000/XP (whatever one you have)
root          (hd0,0)
makeactive
chainloader   +1

```
Don't forget to save the file!

as long as you have windows on the first partition that should work.

---

### Post by bchivers on 2007-02-19
Windows is on rdisk(2) partition(1), how do I add that to the code?

---

### Post by tubasoldier on 2007-02-19
> **bchivers said:**
> Windows is on rdisk(2) partition(1), how do I add that to the code?

it should be (hd1,0) instead of (hd0,0)

But you can read up on it. [GRUB CONFIGURATION]("http://www.gnu.org/software/grub/manual/html_node/Configuration.html#Configuration")

---

### Post by bchivers on 2007-02-19
That didn't work. Checked my computer and it is listed as sdc5. How do I add this to the code. Am reading the link you gave me, thanks. It hasn't made any sense to me yet but I will keep reading it.

PS, It boots to the point where it says "Starting..." and then hangs.

---

### Post by tubasoldier on 2007-02-19
Yeah, it should still be listed as hd*,* under grub.
basically it is this:
sda = hd0
sdb = hd1
sdc = hd2  
ect....

As for partitions it goes like this
sda1 = hd0,0
sda2 = hd0,0
sdb5 = hd1,4
sdc5 = hd1,4

At least that is my understanding of it. Give it a try and see how it goes. Also it would be good to read all that documentation. Because then you will know Grub really well. Education is the key to understanding.

---

### Post by Deinumite on 2007-02-19
Another thing you could try is installing GAG [http://gag.sourceforge.net/]("http://gag.sourceforge.net/")

Just put on a floppy or cd or what have you, and boot from it, and you can configure your own easy to use boot loader

saved me when i deleted my ubuntu partition...but i forgot to fix the grub loader (woops heh)

---

