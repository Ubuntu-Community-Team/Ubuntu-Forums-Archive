---
title: "Installed Fedora 8 and now Ubuntu is lost"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by slobodan on 2007-11-09
I've just installed Fedora 8 KDE werewolf from live cd . The problem is that now Ubuntu doesn't boot. How to fix the problem? I have Ubuntu 7.10.

thanks
Slobodan

---

### Post by Paul820 on 2007-11-09
Get this [http://supergrub.forjamari.linex.org/#help]("http://supergrub.forjamari.linex.org/#help")
Apparently others are having the same problem [http://ubuntuforums.org/showthread.php?t=607301]("http://ubuntuforums.org/showthread.php?t=607301")
I downloaded it and i have not installed it yet. I don't think i will now.

---

### Post by Maestro23 on 2007-11-09
> **Paul820 said:**
> Get this [http://supergrub.forjamari.linex.org/#help]("http://supergrub.forjamari.linex.org/#help")
Apparently others are having the same problem [http://ubuntuforums.org/showthread.php?t=607301]("http://ubuntuforums.org/showthread.php?t=607301")
I downloaded it and i have not installed it yet. I don't think i will now.

Hmm.. I was going to try and play with that this weekend.  Might just hold off now.:)

---

### Post by rsambuca on 2007-11-09
> **Maestro23 said:**
> Hmm.. I was going to try and play with that this weekend.  Might just hold off now.:)

Don't worry, just have the Fedora installer put grub onto it's own partition and add it to your Ubuntu grub manually to chainload the distros.  A lot easier that way.

---

### Post by Maestro23 on 2007-11-09
> **rsambuca said:**
> Don't worry, just have the Fedora installer put grub onto it's own partition and add it to your Ubuntu grub manually to chainload the distros.  A lot easier that way.

Ah, thanks rsam.  I was thinking along those lines, but wasn't sure.

Cool.:guitar:

---

### Post by James79 on 2007-11-09
> **rsambuca said:**
> Don't worry, just have the Fedora installer put grub onto it's own partition and add it to your Ubuntu grub manually to chainload the distros.  A lot easier that way.

I have 2 Ubuntu partitions, both XFS. Grub is setup on it's own ext3 parition. To install the second Ubuntu, I told the install *not* to install a boot loader, and I edited grub manually to include it from my original install and that worked beautifully.

With F8, is it possible to tell it NOT to modify my boot record? I have a feeling that if I do what you suggest, it'll overwrite the boot record to point to its own partition and then I'll loose my original boot menu.

I suppose I could alter this after the fact (I don't know how), but I would rather if F8 leaves well enough alone and just installs itself and I'll add it manually. Does anyone know if this is possible?

---

### Post by PmDematagoda on 2007-11-09
I had the same problem with Fedora 8 myself, I fixed it by using the SuperGrub CD to restore the Ubuntu boot-loader, and then I simply added the entry that was given for Fedora in /boot/grub in the Fedora root and now I can successfully boot between Ubuntu 7.04, Ubuntu 7.10 and Fedora 8.

Hope this helps.

---

### Post by slobodan on 2007-11-09
I've played with werewolf but I decided to keep only Ubuntu.
I've deleted the werewolf partition and installed  XP again , that was Xp partition previously. I reinstalled grub with live cd as per
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
No GRUB says that it can't mount the partition . 
What's wrong?

Slobodan

---

### Post by rsambuca on 2007-11-09
> **PmDematagoda said:**
> I had the same problem with Fedora 8 myself, I fixed it by using the SuperGrub CD to restore the Ubuntu boot-loader, and then I simply added the entry that was given for Fedora in /boot/grub in the Fedora root and now I can successfully boot between Ubuntu 7.04, Ubuntu 7.10 and Fedora 8.

Hope this helps.

The problem with that method is that you will have to manually edit the grub everytime Fedora updates it's grub.  I think it is much easier to chainload the grubs so you only have to edit your grub once.

---

### Post by PmDematagoda on 2007-11-09
I think you are right rsambuca, but the thing is that it was necessitated for me as I have never updated Fedora. But I will be giving chain loading a try now. Thanks for the advice:).

---

