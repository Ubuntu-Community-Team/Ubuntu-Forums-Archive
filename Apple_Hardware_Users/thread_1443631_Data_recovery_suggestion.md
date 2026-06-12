---
title: "Data recovery suggestion?"
date: 2010-03-31
forum: Apple Hardware Users
---

### Post by japhyr on 2010-03-31
Hello,

My wife accidentally deleted all the images from her macbook, and had no prior backups.  I want to try to recover some of them, and I think it should work because she hasn't used the computer much since then.  I've read a bit about the process, but can someone suggest a couple clarifications?
[LIST]
[*]Would it be easier to install a recovery program on my ubuntu box and connect to her macbook for the recovery, or use a livecd directly on her machine?
[*]I've looked at magicrescue and testdisk/photorec.  Any suggestions on which of these to start with?
[/LIST]

Thank you for any suggestions; by the way I am quite comfortable on Linux, but fairly unfamiliar with navigating a mac.

---

### Post by oswaldkelso on 2010-03-31
From what understand testdisk/photorec is the tool for the job. But here's some more should you want to try them.

[http://www.mondorescue.org/](http://www.mondorescue.org/)
[http://www.gnu.org/software/ddrescue/ddrescue.html](http://www.gnu.org/software/ddrescue/ddrescue.html)

---

### Post by ajgreeny on 2010-03-31
DO NOT INSTALL ON TO THE MAC!!!

That may overwrite files and then they are gone for good.  I would suggest a live CD is best, as that will write nothing to the disk and give you a better chance of recovery.

As for the application(s) to use, I would also suggest you look at Testdisk and photorec, the latter of which was originally for recovery of photos from memory cards, but has now become good for almost any file type and system.  Unfortunately it may find masses of randomly named/numbered files which you will then need to search through.

---

### Post by japhyr on 2010-03-31
> DO NOT INSTALL ON TO THE MAC!!!

That may overwrite files and then they are gone for good. I would suggest a live CD is best, as that will write nothing to the disk and give you a better chance of recovery.


This is part of what I'm trying to clarify.  I know not to use the mac as is, because that overwrites the files I want.  I know that using the livecd loads ubuntu into RAM, so that is safe.  But what happens when I use the mac, running the livecd, to connect to the internet and install testdisk through synaptic?  Does testdisk get installed into RAM?  Is it better to install testdisk on my ubuntu laptop, and connect to the mac hard drive through firewire or something like that?

---

### Post by aysiu on 2010-03-31
Yes, loading a live CD is the way to do it. Install the *testdisk* package and then use ```
sudo photorec
``` to get the deleted files back.

More details (with screenshots) here:
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

---

### Post by japhyr on 2010-04-03
> More details (with screenshots) here:
[http://www.psychocats.net/ubuntucat/...rdeletedfiles/](http://www.psychocats.net/ubuntucat/...rdeletedfiles/)

We are following these directions, and it looks like it is going to be a pretty good recovery.  The program is listing 2547 jpg's recovered so far.

I have one question in the middle of all this, though.  I connected a new external drive to store the recovered files, but it was an ntfs file system.  I forced the mount.  When we hook the external drive up to the mac when we are all done, will the mac be able to read from the ntfs external drive?  If not, should we abort the recovery, format the HD from the mac, then start over again?

---

### Post by new_tolinux on 2010-04-03
I don't know anything about MAC's, so I'm not going to say anything about that.

I do know that you should finish the recovery. When it comes to recovery, the sooner the better.

If the Mac would not read the NTFS-drive, you're better of reading the drive by that live-cd or another machine, then copy it from the NTFS-drive to that machine and after that reformat the NTFS-drive.

---

### Post by aysiu on 2010-04-03
Macs cannot read NTFS by default. There may be a helper application you can install to read NTFS, though.

---

### Post by srs5694 on 2010-04-04
> **aysiu said:**
> Macs cannot read NTFS by default. There may be a helper application you can install to read NTFS, though.

This isn't true of recent versions of OS X. A quick Google turns up [this post](http://www.macosxhints.com/article.php?story=20050521110452194) about NTFS support in OS X 10.4.1 (the latest version is 10.6.3). I've personally used the support in 10.5 and 10.6 versions of OS X. Note that this is *read-only* support, but that's all that japhyr needs. For read-write NTFS support in OS X, Paragon has a [commercial NTFS driver,](http://www.paragon-software.com/home/ntfs-mac/) and the [MacFuse](http://code.google.com/p/macfuse/) tool enables use of NTFS-3g (the same source of NTFS support that Ubuntu uses).

---

