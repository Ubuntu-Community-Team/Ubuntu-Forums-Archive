---
title: "gparted broke my macbook :("
date: 2010-12-18
forum: Apple Hardware Users
---

### Post by nukularpowar on 2010-12-18
Hello all.  Hoping someone here can enlighten me on what might have gone wrong with my macbook (running Ubuntu.)

I decided I wanted to have a windows 7 partition for playing games on my bigscreen.   Ubuntu was already installed (yes, I know it's bad to have Ubuntu installed before Windows, but hey, I've done it plenty of times that way on my PC with only a quick Grub fix required.)   However, as I have learned, macbooks are not PC's  :/

Anyways, I loaded GParted from the live cd and went to edit the partitions.   Here is what I saw (more or less)

Dev/sda1:  1 mb, boot_grub off to the side
dev/sda2:  main partition
dev/sda3:  swap

So I shrunk sda2 and created an sda4, which I made ntfs.  After this operation was ***plete, there was an exclamation point next to sda1 in the list.  I had no idea what that meant, and figured I'd be reinstalling grub anyways, so I ignored it and rebooted the ***p.

Now, the problem appears;  the ***puter won't boot, or do anything but sit there with a folder icon with a question mark inside it.  It loads from live cd, and I can see all the files on the partitions, but apparently the boot partition is not being recognized.  Loading GParted still shows that exclamation point beside sda1.

On a sad note, I can't even install windows 7 on that partition, because the drive is GPT, the ***p is 64 bit, and I only have a 32 bit copy.  Guess I should have checked that out before I started (though I had never even heard of GPT before, not being a mac guy.)

Any help would be greatly appreciated!  THank you for your time.

edit:  Would reinstalling Grub on the 1st partition work?  I can't see it in live cd mode and given the exclamation mark I'm not sure that I should try.

edit2:  I guess a more accurate thread title would have been "I broke my Macbook with gparted"

edit3:  No apple OS cd available

---

### Post by Ceyx on 2010-12-19
Is this an Intel Machine ?

If you know how to use the torrent client "Transmission"  you can probably find a Mac OS boot ISO on the net....

I have an old PowerBook G4 running Linux.  If you have an older machine I could probably help, if an Intel probably not ...

---

### Post by nukularpowar on 2010-12-19
I've never heard of transmission, but I'll look it up.   I'm not actually sure if it's Intel or not though, since it's not actually my comp - I'll go have a look at it.

Anyone know what I did wrong with GParted...?  Or is trying to repartition a GPT drive just a no-no?

---

### Post by nukularpowar on 2010-12-19
It doesn't have any intel markings, just says macbook pro under the screen.

---

### Post by srs5694 on 2010-12-19
Your problems are almost certainly related to a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) configuration. As the site I just referenced details, hybrid MBRs are ugly and dangerous. When you changed your partitions, chances are GParted changed the disk from being a hybrid MBR disk to being a legal GPT disk, and this probably broke your boot loader. The solution, ugly as it is, is to re-create a hybrid MBR (using gptsync or [gdisk](http://www.rodsbooks.com/gdisk/)). The hybrid MBR only need to contain the Windows partition(s) and any shared-data partition(s) that must be accessible by Windows; OS X and Linux are both capable of handling the GPT side, and so their partitions don't need to be in the hybrid MBR. It's likely you'll need to re-install rEFIt and/or GRUB once you've created a new hybrid MBR.

---

### Post by srs5694 on 2010-12-22
> **emiledevoss said:**
> Otherwise... bring it to a mac store?

I wouldn't trust the people there to know how to deal with anything Linux-related.

---

### Post by skullmunky on 2010-12-28
I wouldn't trust the people there to know about anything other than being cheerful and peppy :D 

I think srs5694 is right, it's a GPT/MBR sync problem.  btw, It looks like you didn't have OSX anywhere on the machine at all, is that right?  I didn't see an EFI partition in that list either.  

gptsync doesn't look hard to use; I haven't tried it before but it looks like you could just boot to the live CD and do 

```

sudo gptsync /dev/sda

```

and see if that helps.  

Cheer up, I think you should still be able to install Windows though.  If this works and you can recreate a valid MBR mirror of the GPT table, then Windows should be ok with it; and, I'm 99% sure 32 bit Windows will still work a-ok on a 64 bit intel mac.  The intel x86_64 architecture is backwards compatible.  You can also run 32 bit linux distros on 64 bit chips, no problem.

---

