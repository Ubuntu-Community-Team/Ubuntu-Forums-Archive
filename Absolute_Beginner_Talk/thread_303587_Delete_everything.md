---
title: "Delete everything"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by 0m3n on 2006-11-20
hey everyone, i've had a few problems with the browswer messing up already and i think i might have left windows pro on my computer also... so im just going to reinstall ubuntu. Is there a program or somethin i can use to completley wipe everything off my hd?

---

### Post by LLRNR on 2006-11-20
If I get this right, you'd need to *format* your HDD...

---

### Post by 0m3n on 2006-11-20
if that will delete windows and ubuntu and allow me to install a fresh new OS then yes :D

---

### Post by dca on 2006-11-20
...the Ubuntu liveCD does that (re-partition & format) when selecting 'erase entire HDD for installation' option...  hmmm, now I don't remember...

---

### Post by LLRNR on 2006-11-20
If you indeed you want to wipe everything off your HDD, then that's what you should do. But think twice before doing so : if you find out at a later time that you also need XP installed on your machine, I'd suggest you install it first and Ubuntu second. Because if you "switch" these steps i.e. install Ubuntu first and XP second, you should know that Windoze has the bad habit of overwriting the MBR of your HDD, such that you won't be able to boot Ubuntu anymore... Of course there's a wordaround for this, but nevertheless it's a lot more easier to stick to a "traditional" way of installing.

If however you're sure you only want Ubuntu, then you should format all your HDD and go for ext3 filesystem (there are others too but... I haven't tested them yet and however ext3 is the default filesystem for Linux). For help with partitioning you could try [this](http://ubuntuforums.org/showthread.php?t=282018) and [this](http://www.ubuntuforums.org/showthread.php?t=286303). You should be able to format your HDD within the Live CD... but before take a look at those links.

HTH,

LLRNR

---

### Post by LLRNR on 2006-11-20
> **dca said:**
> ...the Ubuntu liveCD does that (re-partition & format) when selecting 'erase entire HDD for installation' option...  hmmm, now I don't remember...

Yup, I can confirm that. It *does* have an option on formatting the whole HDD for you... :D

---

### Post by HereInOz on 2006-11-20
Yes, the installation of Ubuntu gives you the option to Erase the Entire Hard Disk.  If you select that, all will be gone.

If you install Ubuntu but find that you need to use XP for some things, there is an alternative to dual booting.  You can always install VMWare server and run XP in a virtual machine on Ubuntu.  This works quite well unless you need 3D graphics on XP - VMWare won't do that.

Check this link -
[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)
for a "how to" on this.

---

### Post by 0m3n on 2006-11-20
hmmm i think i did do the erase entire HDD for installation, the only reason i think that windows might still be on here is that when i open the disk usage analyzer it only shows that i have 33.5GB when i have a 80GB HD... is that normal?

---

