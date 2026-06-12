---
title: "Just for sake of clearing things up, question about order of installation."
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-02-01
I was just thinking, if you have windows and ubuntu sharing a drive, and something happens to windows and you have to reinstall it, even if you format that partition and reinstall windows on it, you still have the bootloader issue, right?

So if you run into that problem where reinstalling windows is a MUST, I guess you'd just reinstall windows, THEN get the alternate CD for linux and reinstall grub. Correct? Is that right?




Reason I ask is the other day I took dapper out to put edgy in, and grub got messed up and refused to boot anything (said no valid partitions or something). I guess grub was still trying to boot dapper when I had edgy now. When I tried to reinstall grub, I got error code 20. I'm hoping it was a freak thing, and hoping that if I ever have to reinstall windows it should be relatively easy to deal with grub. Eh?

---

### Post by Shatrat on 2007-02-02
Windows will hose Grub when it installs itself, but assuming you dont format the partitions that ubuntu are on you can easily reinstall grub after youre done reinstalling windows.
It should be as simple as running the LiveCD and running "grub-install" from a terminal.
That said, I haven't needed to do this in a while so there might be a better way.

---

### Post by rccharles on 2007-02-02
> **Roasted said:**
> I was just thinking, if you have windows and ubuntu sharing a drive, and something happens to windows and you have to reinstall it, even if you format that partition and reinstall windows on it, you still have the bootloader issue, right?

So if you run into that problem where reinstalling windows is a MUST, I guess you'd just reinstall windows, THEN get the alternate CD for linux and reinstall grub. Correct? Is that right?




Reason I ask is the other day I took dapper out to put edgy in, and grub got messed up and refused to boot anything (said no valid partitions or something). I guess grub was still trying to boot dapper when I had edgy now. When I tried to reinstall grub, I got error code 20. I'm hoping it was a freak thing, and hoping that if I ever have to reinstall windows it should be relatively easy to deal with grub. Eh?

Another option, would be to use superGrub. This has grub on a bootable CD. In a series of menus, superGrub lets you boot any partition.

Main page:
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

download page:
[http://forjamari.linex.org/frs/?group_id=61](http://forjamari.linex.org/frs/?group_id=61)

superGrub can be a little cryptic, but looking at the screenshot page helps.

[http://supergrub.forjamari.linex.org...on=screenshots](http://supergrub.forjamari.linex.org...on=screenshots)

You cursor down to the line you want.

The help line is
| ================> Windows <=============== |

You cursor down below this line and press enter.

I wrote superGrub out to cd and it worked for me. You can boot your partition even without grub on the partition.

...

A harder way would be to use the Unix dd command to make a copy of the boot sector.  You have to boot the live cd to restore the boot sector.


Robert

---

### Post by Roasted on 2007-02-02
So just to clarify, the simplest thing I can do is boot to the live cd, open a terminal in the gui, and type grub-install? That's it?

---

