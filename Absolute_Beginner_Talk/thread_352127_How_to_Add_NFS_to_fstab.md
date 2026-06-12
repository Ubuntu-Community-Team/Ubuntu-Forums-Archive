---
title: "How to Add NFS to fstab"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by l951b951 on 2007-02-02
Hello everyone.  My roommate just bought a HP MV2020 mediavault.  
I am having a hard time finding the exact fstab entry to mount this NFS network drive.  I manually mounted it using > # mount -t nfs hpmediavault:/shares/Volume1/Backup /media/vault/Backup


What should my fstab entry look like?

---

### Post by pseudonym on 2007-02-02
See [this]("http://nfs.sourceforge.net/nfs-howto/ar01s04.html#mount_options") - from the Linux NFS Howto.

---

### Post by K.Mandla on 2007-02-02
My fstab usually looks like this.

```
192.168.1.99:/media/hdc1 /media/share nfs rsize=8192,wsize=8192,timeo=14,intr
```
That's more or less straight out of the [NFS howto]("http://www.ubuntuforums.org/showthread.php?t=249889") here in the forum.

---

### Post by l951b951 on 2007-02-03
Follow up question:  If I edit the fstab on my laptop and then take it to a different network (that doesn't contain the machine referenced in the fstab) will it cause serious problems at bootup?  And will it work again when I bring it home?

---

### Post by pseudonym on 2007-02-03
> **l951b951 said:**
> Follow up question:  If I edit the fstab on my laptop and then take it to a different network (that doesn't contain the machine referenced in the fstab) will it cause serious problems at bootup?
No, I don't think so. There'll be an error message about not finding that shared drive but it shouldn't halt the boot process. But if you're concerned you can just comment your nfs share out temporarily.
 
> **l951b951 said:**
> And will it work again when I bring it home?
There's no reason why it shouldn't.

---

### Post by lee810 on 2007-02-12
> **l951b951 said:**
> Hello everyone.  My roommate just bought a HP MV2020 mediavault.  
I am having a hard time finding the exact fstab entry to mount this NFS network drive.  I manually mounted it using 

What should my fstab entry look like?

I am one of the HP Media Vault's designers and I maintain a FAQ/Knowledgebase for it along with a user group.  The answer to this question is given here:

[http://www.k0lee.com/hpmediavault/index.html#nfs](http://www.k0lee.com/hpmediavault/index.html#nfs)

Specifically:
------------------------------------
If you would like your Linux system to automatically mount the Media Vault whenever it reboots, you can add this entry to /etc/fstab

hpmediavault:/shares/Volume1/FileShare /mnt/mediavault nfs

Please note, your Linux distribution may require a different order that what is shown above.  That order works on Ubuntu.  After adding the line to the /etc/fstab file, you can run the following command to get it to process the fstab file:

mount -a

-------------------------------------

Lee Devlin
[http://www.k0lee.com](http://www.k0lee.com)

---

