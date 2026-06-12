---
title: "Cleanly Mounting Windows Shares"
date: 2005-09-15
forum: Absolute Beginner Talk
---

### Post by salvatore on 2005-09-15
I installed Breezy a few days ago and am impressed with the clean look and ease of use.  Thanks to help from these boards Ive been able to get my wireless adapter working as expected; the remaining hurdles are those tweaks to emulate/replace the niceties offered in Windows.

For this post, Im referring specifically to mounting shares on other Windows machines.  From the command line, as root, I can issue a properly formatted smbmount command and get to a known Windows share as expected.  Using the Places launcher, using the same username, domain, and password parameters, Im not.  It either seg faults or loops the username/domain/password dialog box.  I imagine this is due more to a local permissions issue than to a legitimate issue with Ubuntu.

In Windows, I can create a shortcut to a particular share and upon opening that shortcut, if I need to authenticate Im presented with a dialog asking me to do so.  In Ubuntu Ive created a shortcut to the local mount point for the Windows share, but unless I use the command line (as root, or via sudo) to authenticate ahead of time, its an empty folder.  The question becomes, how does one envoke the smbmount/smbclient command as a normal user and pass the authentication credentials in one fell swoop?  Ive tried a CTRL-L in Nautilus and entering the network share name directly, but that doesnt act as expected.

Assumptions:
* The Windows share is valid and accessible from the current location.
* All of these appear to be Linux issues and not explicitly Ubuntu issues; Ubuntu is just the distribution.
* Close approximations to Windows behavior are valid substitues.  Im looking for ways to use the Ubuntu installation instead of dual booting with XP.

Questions:
* What's the best way to authenticate, mount, and read/write to a Windows domain share on a regular basis?
* Must one be root to use smbmount/smbclient?
* How are others doing these same tasks?

Thanks in advance.

---

### Post by davmac on 2005-09-16
Have you seen this section of the starter guide? [http://ubuntuguide.org/#automountnetworkfoldersall](http://ubuntuguide.org/#automountnetworkfoldersall)

Does this cover it?

Dave Mac

---

### Post by salvatore on 2005-09-16
On first glance it appears to cover my questions (and then some); thanks for pointing it out.

I promise to read thoroughly before posting again.  Is it safe to assume most, if not all, of the details in that guide will work with Breezy as well?

---

### Post by davmac on 2005-09-20
Salvatore,

No problem at all. That's what the forum is here for! As far as I can tell, most of the advice in the starter guide still applies to Breezy.

Dave Mac

---

### Post by salvatore on 2005-09-20
[QUOTE=davmac]As far as I can tell, most of the advice in the starter guide still applies to Breezy.[/QUOTE]It does indeed, as Ive run through it a few times with my Breezy install and have yet to encounter a problem.

Thanks again.

---

