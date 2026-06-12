---
title: "How to upgrade Evince and File Roller on Feisty"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by MockY on 2008-02-04
I have looked everywhere but still haven't found a solution

How on earth do I upgrade Evince and File Roller on Feisty?
Right now I run :

Evince 0.8.1
File Roller 2.18.1

Reasons being that I can't drag-n-drop when unpacking in File Roller and to enable scroll in Evince. 

I just installed 7.04 on my laptop and after all auto upgrades, I have a later version of Evince since I can scroll. So I know it can be done. But how?

---

### Post by Blutack on 2008-02-04
Is there any reason you don't want to upgrade to 7.10, which would ensure you have the latest and greatest of everything?

---

### Post by MockY on 2008-02-04
I knew this question would come up and I hoped that the issue would be addressed instead. What version I run have nothing to do with the fact that I want to upgrade these two packages only, but here it goes;

On my main system, Gutsy crashes randomly, programs hangs and crashes and the system is over all buggy. Even after a fresh install. On my laptop, I have to have the power chord plugged in at all time, otherwise all I get is a  black screen. However Xubuntu 7.10 works without it (indicating something buggy with power management in Gnome), but instead the OS is not at all stable (random crashes and so forth)   Since Feisty runs as stable as it should, installing software that is better in later versions of Ubuntu and Gnome is of great interest.

So does anyone tried and succeeded with this? Like I mentioned before, a later version of Evince (that supports scroll) got automatically installed when I installed Feisty on my laptop the other day, so I know at least Evince should work to upgrade.

---

### Post by Blutack on 2008-02-04
Ok, sorry!  Just had to make sure, a lot of Ubuntu: The Free OS type guides are still knocking around linking to 7.04.
Have you enabled backports in Software Sources and tried updating again?

---

### Post by MockY on 2008-02-04
No I'm sorry. Had a bad day today and I had no right to transfer that into the post.

OT:
Yes, the backports are enabled.

---

### Post by Blutack on 2008-02-04
It's cool, happens to us all.  If both computers are running feisty, they both have the same sources enabled and you have run
sudo apt-get update && sudo apt-get upgrade
on them both they should have identical package versions unless one is 64bit or PPC.
You could have a look in /var/cache/apt/archives
on the laptop with the versions you want, put the files on a usb stick and install them manually, but that is a rather dirty workaround.
The other thing to check would be to make sure your desktop has all the sources enabled and definately working...could you post you /etc/apt/sources.lst from both machines please?

---

