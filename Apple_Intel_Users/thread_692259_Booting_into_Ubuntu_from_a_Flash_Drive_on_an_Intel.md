---
title: "Booting into Ubuntu from a Flash Drive on an Intel Mac"
date: 2008-02-09
forum: Apple Intel Users
---

### Post by Audacitor on 2008-02-09
Okay, so I've been trying all day to find a way around this problem.  I've posted on the Apple Discussion forums, called Apple Tech Support, and perused at least 7 different Google searches, but I have not found the answer.

I downloaded the i386 version of Gutsy, burned it to a disk, and successfully started a Live Session.  "Awesome," thought I, "for in my first 15 minutes ever with Linux, I got a functional system."  However, booting Ubuntu from a Live CD is slow, and it'd be much faster if I could do the same thing from a flash drive.  And even better, with a flash drive, I would have space leftover for my own files.  I could carry my own system with me, and use it on pretty much any computer anywhere (I don't have a laptop).  I might never have to deal with Windows ever again.  Just OS X and Linux.  A perfect world!

Except that BootCamp will not recognize Ubuntu from a flash drive on an Intel Mac.  From what research I've done, this is apparently Apple's doing.  So I thought, "Okay, no problem, we'll cut the problem off at BIOS and go from there".   It was then that I realized that Macs don't have a BIOS.  They use something called EFI instead.

More digging, and I've found this tool called Refit.  However, given that this tool obviously plays with the guts of the computer, I'm not willing to experiment with it without guidance from people who know what they're doing (that's [hopefully] you guys).

I've been using Ubuntu for almost two days now, and I love it.  I've never met on operating system that's just different.  Not inferior, not superior, just different (sidenote, I'm comparing Ubuntu to OS X, which is what I've used for eight years now.  Both Ubuntu and OS X blow any Windows sytsem out of the water).  I'm working hard to get my bearings inside the community and just generally get in the flow, so to speak.  I understand that this question may have been previously answered (I did search the forums, and I found an article that covered booting from a USB 2.0 external hard drive, but that's not quite my problem), so I offer my sincerest apologies if that is the case.  Hopefully by this time next week I won't be quite so blind as to where to get help, and have a decent enough comprehension of Ubuntu to figure most problems out on my own.

Thanks guys,
Audi

---

### Post by cyberdork33 on 2008-02-09
> **Audacitor said:**
> More digging, and I've found this tool called Refit.  However, given that this tool obviously plays with the guts of the computer, I'm not willing to experiment with it without guidance from people who know what they're doing (that's [hopefully] you guys). This is incorrect. It does not "play with the guts of the computer". It is an EFI executable that starts a menu boot-chooser, that is all, and is easily uninstallable. It will not rectify your situation, but it may help if you are planning to try and get it working anyway.

> **Audacitor said:**
> I understand that this question may have been previously answered (I did search the forums, and I found an article that covered booting from a USB 2.0 external hard drive, but that's not quite my problem), so I offer my sincerest apologies if that is the case.Same thing. booting from a device that has a USB interface to your mac is, essentially, a USB harddrive. All the information of anyone that has tried this is in the thread you are referring to. that is the best information that we can offer you on the subject.

---

### Post by Audacitor on 2008-02-09
Well, rEFit is definitely a step in the right direction, but the thread that covers booting from external devices gets a bit too techie for me around the part where they start talking about GRUB.  I'm looking at this:

[QUOTE=kson]I just got it to work on my Macbook C2Duo 2.0!

Nothing worked until I used a 100mb big partition on my main harddrive as /boot and installed grub on that instead of any MBR. Now Refit shows Mac, Win and Linux on the main drive. Then grub is responsible for loading ubuntu from the external drive.

Now I got MacOSX, Windows XP and /boot on the internal 80gb drive and Ubuntu on an external 300gb drive.

Happy Days! Ubuntu works great on a Macbook! Even my bluetooth mouse![/QUOTE]

If I'm reading this correctly, kson had to make an new partition in his hard drive that the computer would automatically boot into (/boot).  Inside, he placed something called GRUB, and this seems to fix everything.

This worries me.  If I have to partition the hard drive of every Mac I want to boot Ubuntu on, there's hardly a point in trying at all; too time consuming.  Should I give up now, or am I reading this wrong?

Thanks again for the help,
Audi

---

### Post by cyberdork33 on 2008-02-09
> **Audacitor said:**
> If I'm reading this correctly, kson had to make an new partition in his hard drive that the computer would automatically boot into (/boot).  Inside, he placed something called GRUB, and this seems to fix everything.

This worries me.  If I have to partition the hard drive of every Mac I want to boot Ubuntu on, there's hardly a point in trying at all; too time consuming.  Should I give up now, or am I reading this wrong?
You are pretty much right on. The only benefit this method gives you is that you can keep more space free on your internal hard drive. Grub is the standard Ubuntu bootloader which loads the linux kernel into memory. Every install of Ubuntu uses it. Really the key is that you are creating the partition for the boot directory of your linux install on the internal drive. For some reason the Mac EFI firmware will not boot "legacy" bootloaders from an external drive. You can complain to apple if you would like. There are some bug reports against refit about this, and if you look through them, they basically say they can't do anything about it.
[http://sourceforge.net/tracker/?group_id=161917&atid=821764](http://sourceforge.net/tracker/?group_id=161917&atid=821764)

---

### Post by Audacitor on 2008-02-10
Well, I'm pretty much resigned to the fact that I won't be able to get this working, but I still want to pick apart the why it won't work, if that's okay.

You said Grub is used by every Ubuntu installation to boot it up.  What about LiveCDs?  What do they use?  Because that's pretty much what I did for my flash drive; threw the contents of the LiveCD on it.

If a LiveCD needs Grub, then why don't I have to partition my hard drive and set up Grub for it?
If a LiveCD doesn't need Grub, then why does an exact copy of it's contents need it on a flash drive?

---

### Post by lomlate on 2008-02-10
the thing about is: apple will look at a cd as a "bootable drive" then linux can do its bit. If you have linux on a partition it will recognise it as a "bootable drive" then linux can do it's bit. However apple refuses to look at external drives as "bootable drives"

---

### Post by cyberdork33 on 2008-02-10
> **lomlate said:**
> the thing about is: apple will look at a cd as a "bootable drive" then linux can do its bit. If you have linux on a partition it will recognise it as a "bootable drive" then linux can do it's bit. However apple refuses to look at external drives as "bootable drives"It is USB/Firewire that is the issue I think... It will in fact, see it as bootable just fine, it will just fail to boot when you try to boot it. OSX will boot from an external drive just fine.

I am unsure what the CDs use... There is another bootloader that is used for linux CDs... You can use grub for a cd, but I don't think that is what Ubuntu does.

---

### Post by lomlate on 2008-02-10
What would be the best cd to boot from if I wanted to use a cd as a boot loader to really quickly just be able to boot from the HDD?

Like boot: CD--->external HDD.

I could use ubuntu live but I don't want to wait all the time it takes to boot. A short boot time with no features except: boot to the external would be great.

---

### Post by Audacitor on 2008-02-11
Well, thanks for you help everyone.  It wasn't really essential that I get Ubuntu to boot from a flash drive on a Mac.  Just PCs and other stuff so I don't have to work with Windows.  I'm determined to get it to work from an external HDD, though, and in addition to the monstrous thread already existing for that, I have some Linux friends down at the Apple Store who can probably help out too.

If I find a solution, I'll post it here.  The current thread seems like it could be overwhelming for a person new to computers.

Thanks all.

---

### Post by cyberdork33 on 2008-02-11
> **lomlate said:**
> What would be the best cd to boot from if I wanted to use a cd as a boot loader to really quickly just be able to boot from the HDD?You would have to create your own cd with grub and the kernel on it. Someone has described how to do that in the main "boot from external drive" thread. You might just be able to use theirs.

> **Audacitor said:**
> Well, thanks for you help everyone.  It wasn't really essential that I get Ubuntu to boot from a flash drive on a Mac.  Just PCs and other stuff so I don't have to work with Windows.  I'm determined to get it to work from an external HDD, though, and in addition to the monstrous thread already existing for that, I have some Linux friends down at the Apple Store who can probably help out too.That would be awesome if they can share any secrets.

> If I find a solution, I'll post it here.  The current thread seems like it could be overwhelming for a person new to computers. If you find a definite solution, I would rather you start a brand new thread and label it has a how to, then I will sticky it in the FAQ in place of the current thread. The thread linked there now, is more of a deterrent to new users on purpose. Basically, if someone really wants it, and is willing to tinker, then they will read it. If it is isn't that important, they will assume it is a no go, and move on.

---

