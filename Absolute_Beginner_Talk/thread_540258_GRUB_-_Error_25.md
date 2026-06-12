---
title: "GRUB - Error 25"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by knabino on 2007-09-01
I am new to having to fix my Ubuntu issues (someone else used to be around to do that).  I went to my desktop machine to turn it on, and it will not boot.  I get:

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 25

Can someone please help me out?  I need to get onto that machine.   Thanks

---

### Post by wireddad on 2007-09-01
Not sure how to fix, but [http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)

---

### Post by Skrynesaver on 2007-09-01
**ERROR ****25** : [B]"Unrecognized command"
[/B]Do you have a live CD about the place?
If so boot off it and take a copy of your /boot/menu.lst and we'll see if we can find out what grub is choking on.

---

### Post by knabino on 2007-09-01
Thanks Wireddad.   So the error I am getting is:

25 : "Unrecognized command"

This error is returned if an unrecognized command is entered into the command-line or in a boot sequence section of a config file and that entry is selected.

Now to figure out how to fix it.   I hope it is not a major issue. anyone?  Not the way I wanted my weekend to start.

---

### Post by knabino on 2007-09-01
> **Skrynesaver said:**
> **ERROR ****25** : [B]"Unrecognized command"
[/B]Do you have a live CD about the place?
If so boot off it and take a copy of your /boot/menu.lst and we'll see if we can find out what grub is choking on.

No, I was not given a live CD.   is this something that I could DL and burn from my laptop or  *choke* the widnows box in the house?   The desktop and the laptop were given to me with Ubuntu already installed on them.

---

### Post by schorsch on 2007-09-01
You can download the Live CD [here]("http://www.ubuntu.com/getubuntu/download"). Burn it as an ISO and not faster than 4x speed.

---

### Post by Skrynesaver on 2007-09-01
As I'm assuming you didn't interrupt the boot sequence and enter a command the error probably lies in your /boot/menu.lst, this is the series of commands that grub reads when booting.  If you boot from the live CD you can then mount your Ubuntu partition and forward a copy of the menu.lst from the /boot/grub/ directory on that partition.  If any of this sounds scary just ask ;)

---

### Post by knabino on 2007-09-01
Thanks, I am DLing it right now (50%) complete and will then get over to the other machine.  Yes, this is scary.  I can not aford to lose anything on that machine :(

---

