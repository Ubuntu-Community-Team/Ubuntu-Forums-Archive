---
title: "Uninstalling programs in Ubuntu/Linux"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2006-09-04
A question about the process of uninstalling application programs in Ubuntu and other Linux distributions.

I am sure that all M/S windows users are aware of how **good** software vendors were at installing their software applications on a M/S operating system computer **BUT** that they in turn were **very poor** when it came to uninstalling their software from that same computer, in that, when you ran the uninstall process, you still had numerous files, folders and other references to that application left in various places on the hard drive.

In Ubuntu and other Linux distributions, does this same problem exist ?

When you uninstall an application in Ubuntu can you count on 100% of the references, etc. to that program being gone ?

Thanks.

---

### Post by xpod on 2006-09-04
After ALL that time i thought everybody would KNOW enough to know to use "aptitude"..as it removes all the dependancies.
AS LONG as you use it to install in the first place that is!

EDIT:.....Mind you i dont know if that means every little trace of an app is gone....Soon find out

EDIT......AHHH,STILL traces left behind after all....I had installed beagle to kubunto with aptitude last night and have just removed it with aptitude
and i can still find files......."inept adept"....mmmmmmmm:confused: .

I think i recall a "purge" command to go with the remove command....mabey THATS whats required??

---

### Post by wpshooter on 2006-09-04
Thanks, I'll take that as a **NO**.

Maybe it's just me, but when I used to write some simple programs in GWBASIC, and when I had to create any intrinsic files during the program, when I got ready to exit the program, I made sure that these temp files were gotten rid of before the program ended and I think that hopefully if I had written a program to uninstall with, that I would have gotten rid of **ALL** traces of the program within the uninstall process, but again maybe that just me.

---

### Post by rohan! on 2006-09-04
if you install via the package manager then you can get rid of the program by typing```
sudo apt-get remove -purge *[COLOR="Red"]progname[/COLOR]*
``` this should remove all of the program including config files etc. i haven't had any problems with this, and don't think that it has left any program files on my computer... but i may be wrong.

---

### Post by slibuntu on 2006-09-04
Wow xpod, i always assumed aptityde did get rid of everything, interesting...

---

### Post by jediborger on 2006-09-04
Ok well under Synaptic there's two options, Remove and Completely remove. Remove justs uninstalls the app and leaves the comfiguration files so they will be there if you reinstall the app, Completely Remove deletes everything including the config files for the app. But also if something doesn't work you can just delete the directory and everything will be fine, no registry to deal with.:)

---

### Post by msak007 on 2006-09-04
> **slibuntu said:**
> Wow xpod, i always assumed aptityde did get rid of everything, interesting...
Aptitude only removes an app's dependencies if they're no longer needed when uninstalling it. You still need the *purge* option to remove any config files as well:
```
apt-get remove --purge <app name>
``` or
```
aptitude purge <app name>

```Either way you do it that should remove all traces of the app.

---

