---
title: "Gnumeric plots bug - running 8.10 through virtualbox"
date: 2008-10-30
forum: Apple Hardware Users
---

### Post by swhit on 2008-10-30
Hello,

Anyone else having problems with plots in gnumeric in 8.10? I can create a plot, but when I select the plot with my mouse, I can't unselect the plot. So the plot just follows the mouse around.

I never had this problem with 8.04.

I've upgraded today (clean install) to 8.10 using virtualbox on mac os x (latest versions of os x and virtualbox). Everything else runs great (except I also can't find g77 in the repos).

I'd switch to OpenOffice, or excel, or numbers (I have them all installed on my machine), but the statistics tools in gnumeric are excellent and I've come to depend on them greatly. So I would rather not switch spreadsheet programs. I guess I can always downgrade to 8.04 ...

Anyone with any idea how I can fix this?

thanks in advance.

---

### Post by cyberdork33 on 2008-10-30
well, i would first try to figure out if it is a problem with gnumeric by itself, or if the problem only occurs when running in VirtualBox. either way, it is likely not a mac-specific issue and you might find more help on this in the main forum.

---

### Post by swhit on 2008-10-31
The problem/bug is specific to virtualbox. I've installed 8.10 directly on a different machine (i.e., not through virtualbox), and have experienced no problems with plots in gnumeric.

---

### Post by cyberdork33 on 2008-10-31
> **swhit said:**
> The problem/bug is specific to virtualbox. I've installed 8.10 directly on a different machine (i.e., not through virtualbox), and have experienced no problems with plots in gnumeric.
In that case, I would check/file bugs in VirtualBox. It is likely a virtual display driver issue.

---

### Post by roberf1 on 2009-01-25
> **swhit said:**
> Hello,

Anyone else having problems with plots in gnumeric in 8.10? I can create a plot, but when I select the plot with my mouse, I can't unselect the plot. So the plot just follows the mouse around.

I never had this problem with 8.04.

I've upgraded today (clean install) to 8.10 using virtualbox on mac os x (latest versions of os x and virtualbox). Everything else runs great (except I also can't find g77 in the repos).

I'd switch to OpenOffice, or excel, or numbers (I have them all installed on my machine), but the statistics tools in gnumeric are excellent and I've come to depend on them greatly. So I would rather not switch spreadsheet programs. I guess I can always downgrade to 8.04 ...

Anyone with any idea how I can fix this?

thanks in advance.

Sorry this is off thread -? bad manners-? swit had the following problem posted with edgy (I now have this problem with hardy) and this posting seemed an effective way to touch base - [email]floyd@Mabels.biz[/email] -newby  -sorry if inappropriate quote of old/new problem follows

While updating the packages the other day using "sudo aptitude update" followed by "sudo aptitude dist-upgrade" I eventually get to:

Setting up linux-image-2.6.17-10-386 (2.6.17-10.24) - new numbers of course
Running depmod.

The computer hangs at this step. I've let it run for over an hour and it still doesn't finish. Basically, I have to Ctrl-Alt-F1 to break out and run "sudo /sbin/shutdown -r now" from the command line to reboot and start over.

Anyone know what's going on? I've been running edgy for about 2 weeks now with no other significant problems. Actually, edgy runs fine now. I just can't update anymore because it hangs on the above mentioned "depmod" step.

Help please? Thanks.

---

