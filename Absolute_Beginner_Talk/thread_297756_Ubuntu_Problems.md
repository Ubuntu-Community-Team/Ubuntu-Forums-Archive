---
title: "Ubuntu Problems"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by 13291 on 2006-11-11
When I try to use Easy Ubuntu after downloading and installing it, it gives me this error:

W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

I also have a problem that sometimes after I shut down Ubuntu, the next time I start my computer up GRUB is messed up.  Instead of choices for Ubuntu, Ubuntu Recovery, Memtest, and Windows; my choices are Ubuntu, Ubuntu Recovery, Ubuntu, Ubuntu Recovery, Memtest, and Windows.  Ubuntu and Ubuntu Recovery show up twice.

---

### Post by ReaderRat on 2006-11-11
A.- KEY Public HowTo get
          **[http://www.ubuntuforums.org/showthread.php?p=1653773#post1653773](http://www.ubuntuforums.org/showthread.php?p=1653773#post1653773)**
B.- That is normal. The second set of items is a different version from the first.

---

### Post by 13291 on 2006-11-11
Thanks for the answer on the first question.

Why does the second set of items exist though.  It works fine with just the first, yet if I delete the second they come back.

---

### Post by ReaderRat on 2006-11-11
There is a reason they are there. I just can't remember why at the moment.

---

### Post by strabes on 2006-11-11
I believe it's because old kernels are still installed after an update. Not sure though.

---

### Post by Tomosaur on 2006-11-11
When a major system update occurs (eg, installing a new kernel), the old kernels are not removed. Generally speaking, you should keep an old kernel version back in case a problem occurs with the new version. Grub doesn't know the difference between kernels apart from their name, so it just puts everything it finds into the menu. You can tell grub to only show 1 kernel, or 2, or whatever, by changing a line in the grub menu.lst. To do this, follow these steps:

Open up a terminal (command line), and type:
```

gksudo gedit /boot/grub/menu.lst

```

Type in your user password, then once you can see the file, do a 'Save As' and back it up somewhere you won't forget. Next, do a search for the line which says:
'#howmany=all'.

Change the word 'all' to an integer of your choice. I have mine set to 2, so I can boot an old kernel version if I want to. Once your're done, save (as menu.lst) and exit. In the command line, type 'sudo update-grub'. If all goes successfully, the next time you reboot, Grub will only show the number of kernels you tell it to.

If you don't feel comfortable doing that, you may want to check the link in my signature.

---

### Post by nanousr on 2006-11-12
If the older kernel is for recovery, then what is the recovery option for?

---

### Post by Tomosaur on 2006-11-12
It's not. The kernel itself may have problems with your hardware, in which case the recovery option itself may not work. An older kernel is a complete kernel, so you can fall back entirely to that kernel until a new kernel is released.

---

