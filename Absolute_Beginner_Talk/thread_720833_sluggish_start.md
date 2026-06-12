---
title: "sluggish start"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by muldengold on 2008-03-10
Hi,
I've just installed Ubuntu 7.10 on my computer and it takes about 2-3 min for the OS to boot (with a black screen). Is that normal? Is it awaiting a time-out for something? Otherwise everything works quite nicely.

Thanks

---

### Post by scragar on 2008-03-10
you could try a few speed up techniques, firstly reboot, and at grub(black screen with OS list, or press "esc to enter grub") use the "e" key to edit the boot line for your normal boot and add " profile" to the end of the line, then hit enter to boot. After it is finished booting your next reboot should be a bit faster.

you could also try removing the word "quite" from the same line as above to see what ubuntu is doing and maybe spot where it's running slow.



if you mess anything up and it doesn't boot don't worry and just restart, your edits to grub are not saved during boot so any changes will be undone (profiling saves info to allow next boots to be quicker, so that change does stay).

---

### Post by muldengold on 2008-03-10
thanks scragar, I'll try.

---

### Post by muldengold on 2008-03-13
I have tried it and even after deleting "quite" and pressing "b" to reboot the the screen stays black. Within the 3min it seems that the hard disk is used only occasionally. Any other ideas???

---

### Post by ugm6hr on 2008-03-13
Try reading the first 2 posts here: [http://ubuntuforums.org/showthread.php?t=581075](http://ubuntuforums.org/showthread.php?t=581075)

---

### Post by muldengold on 2008-03-13
Thanks, I think I'm getting there. Yes, the screen resolution in the usplash.conf is wrong. However I cannot save any changes in that file as I'm told that I do not have permission to do that, although I'm the administrator.

---

### Post by ugm6hr on 2008-03-14
This should allow you to edit it:
```
gksudo gedit /etc/usplash.conf
```

---

### Post by ibizatunes on 2008-03-14
I know it not a fix straight away, but upgrade to 8.04 in a months time, will make ur machine boot fast, and correct the screen resolution problem..... may just be worth waiting for a month....depends on how much of issue it is

---

### Post by ugm6hr on 2008-03-14
> **ibizatunes said:**
> I know it not a fix straight away, but upgrade to 8.04 in a months time, will make ur machine boot fast, and correct the screen resolution problem..... may just be worth waiting for a month....depends on how much of issue it is

This fix will only take 2 minutes!  That is the excess time for a single reboot.

Not sure how often you reboot in a month, but if it more than once, I'd go ahead and fix it ;)

---

### Post by muldengold on 2008-03-14
Thanks everyone, I fixed it, although I didn't know what exactly I was doing when I entered the sudo command line. Is there a tutorial somewhere?

---

### Post by ugm6hr on 2008-03-15
> **muldengold said:**
> Thanks everyone, I fixed it, although I didn't know what exactly I was doing when I entered the sudo command line. Is there a tutorial somewhere?

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

