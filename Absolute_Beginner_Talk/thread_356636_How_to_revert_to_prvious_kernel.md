---
title: "How to revert to prvious kernel?"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by pennyminstrel on 2007-02-08
Could somebody tell me how I revert to a previous kernel? I`ve got a problem I can`t solve and as I upgraded today I thought this might be worth a try, but I can` t find instructions anywhere.

thanks everyone.

Penny

---

### Post by kebes on 2007-02-08
Usually when a new kernel is installed, it is added to the grub list you see at boot time.

So if you reboot your computer, at the grub menu you should see different options for ubuntu with different kernel versions. Select an older one and try booting with that.


If you don't see the grub menu at boot time, that might be because you've set the wait time to zero or something. You can modify the file "/boot/grub/menu.lst" to modify grub behavior.

---

### Post by pennyminstrel on 2007-02-08
Thanks! I`ll try that.

---

### Post by stevelasvegas on 2007-05-28
But what can one do to always boot to a previous kernel without having to enter the grub menu?

Using Ubuntu Feisty 7.04 installed with WUBI.
Update manager checked for updates which I allowed to download and install.
Now, when I boot, the Ubuntu splash screen freezes. I do a ctrl+alt+f1 and it says "Loading, please wait" and stays there.
Can't boot.
This is what it says when booting stops:
I see where it stops booting;
Loading Please Wait....
[43.675877] ATA1.00: SET of native returned 0, expected 195371568
[43.691836] ATA1.00: SET of native returned 0, expected 195371568
Device manager says:
Intel Mobile 915GM/GMS/910GML Express Graphics Controller
is being used.
Aparently, the new kernel doesn't like my graphics card driver; at least that's what some have said.
Anyway, when I boot with the new kernel (I guess that's what you call it), I hit esc, select Ubuntu and when presented with the "kernel menu" I can not get it to boot using 2.6.20-16 but I can using 2.6.20-15.
Any suggestions on what I can do?
I'm a very new Linux user trying to migrate from Windows; very litle Linux knowledge.
Thanks
__________________

---

### Post by drs305 on 2007-05-28
If you mean not having to mess with grub on boot, back up menu.lst first and then read the following. If you don't want to edit the grub boot.lst, go on to the next post.

You can edit the grub boot file (/boot/grubmenu.lst) and eliminate or (better yet) comment out the kernel and recovery mode you don't want to see. You could also change the default entry number (default is 0) to the one that points to the previous kernel (if you don't comment it out).

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst

```

---

