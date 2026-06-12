---
title: "How to fix, please!"
date: 2008-05-10
forum: Apple Hardware Users
---

### Post by Officer Dibble on 2008-05-10
Hi, can anyone tell me what's going on here, please?

This error (see attached image) is occurring in Leopard on a MacBook at boot up. I pressed Command 'S' to get this screen - otherwise it just stays grey after the boot chime and flicks between a 'no-entry' symbol and the Apple Logo rapidly.

Please help.

---

### Post by cyberdork33 on 2008-05-10
please use more descriptive thread titles...

Your system is unable to load the OSX kernel. I would say the file has become corrupted somehow. boot from the OSX disc and repair permissions.

---

### Post by Uinluan on 2008-05-10
It would appear that your system may have crashed.  I would recommend booting from your leopard install disk and trying to repair permissions to that drive and then boot from it to see if it comes up.

---

### Post by Officer Dibble on 2008-05-10
Thanks for such a quick response... still need the the install disk though... grrr. :(

---

### Post by Uinluan on 2008-05-10
If you have another Mac and a firewire you could put the machine that is having the problem in target mode by holding the T button down as it boots until you get the firewire icon floating around on the screen then plug that into your other mac it will show up as a mounted firewire drive. Open up disk utility on the good machine and run repair permission on the drive that has been mounted as a firewire drive from the other machine.  Don't know if you have another Mac but that is another way to do it.

---

### Post by Officer Dibble on 2008-05-10
> **Uinluan said:**
> If you have another Mac and a firewire you could put the machine that is having the problem in target mode by holding the T button down as it boots until you get the firewire icon floating around on the screen then plug that into your other mac it will show up as a mounted firewire drive. Open up disk utility on the good machine and run repair permission on the drive that has been mounted as a firewire drive from the other machine.  Don't know if you have another Mac but that is another way to do it.

That's a brilliant idea, and a fantastic concept on the part of the peoploids at Apple.

As good as the Mac probably is, I don't know any other people that own one... otherwise I would have borrowed their disk by now.

Once again, a brilliant idea, many thanks. :)

---

### Post by cyberdork33 on 2008-05-10
yea basically mounting the disk in some system that is not running from the partition you need to fix will allow you to fix it... You might eeven be able to mount it in linux and fix it, but I am not sure what the permissions need to be... there is a thread in the mactel FAQ that shows how to do a filesystem check from linux, but honestly, I would recommend that method...

---

### Post by russo.mic on 2008-05-11
> **cyberdork33 said:**
> yea basically mounting the disk in some system that is not running from the partition you need to fix will allow you to fix it... You might eeven be able to mount it in linux and fix it, but I am not sure what the permissions need to be... there is a thread in the mactel FAQ that shows how to do a filesystem check from linux, but honestly, I would recommend that method...

can you repair OS X permessions from Linux?  I don't think that would work...

---

### Post by cyberdork33 on 2008-05-11
> **russo.mic said:**
> can you repair OS X permessions from Linux?  I don't think that would work...
yes, should be able to. has to be writable though.

---

### Post by russo.mic on 2008-05-11
Wow, just did it to see CD.  Your right.  you can change a file's permissions in linux, and they carry over to OS X.  I would have thought that wouldn't work for some reason.

Learn something new everyday.

Russo

---

### Post by Officer Dibble on 2008-05-16
> **Uinluan said:**
> It would appear that your system may have crashed.  I would recommend booting from your leopard install disk and trying to repair permissions to that drive and then boot from it to see if it comes up.

Didn't work... still having the same problem... however, now that I have an Install Disk I can provide any logs necessary to hopefully resolve this. :)

Any further suggestions? :confused:

---

### Post by neorou on 2008-05-16
OK. Just a long-shot, but have you tried zapping PRAM and maybe even clearing the NVRAM? Also, if you boot from the Ubuntu CD will it boot normally?

---

### Post by Officer Dibble on 2008-05-17
> **neorou said:**
> OK. Just a long-shot, but have you tried zapping PRAM and maybe even clearing the NVRAM? Also, if you boot from the Ubuntu CD will it boot normally?

Yep, I've cleared PRAM and NVRAM, and Ubuntu LiveCD (8.04) will boot without issue.

As a result of booting into Ubuntu I found what could be an unusual boot configuration while checking things out with Gparted:

> /dev/sda1 fat32 Size=200MB Used=18MB Unused=181MB boot
/dev/sda2 HFS+ Size=105.88MB Used=24.91GB Unused=80.97GB
Unallocated 128MB
/dev/sda3 fat32 Size=5.6GB Used=11.63MB Unused=5.58GB msftres

Does anything look unusual to you about this?

Journalling is enabled and I don't know how to disable this - so it's not allowing me to write to the HDD.

---

### Post by cyberdork33 on 2008-05-17
> **Officer Dibble said:**
> Does anything look unusual to you about this?No

If repairing the volume didn't work then I think you are going to have to take more drastic measures... like copying the kernel off your OSX DVD or restoring a backup or reinstalling.

See the "**Advanced alternative**" portion of this page for getting a new copy of the kernel:
[http://docs.info.apple.com/article.html?artnum=106805](http://docs.info.apple.com/article.html?artnum=106805)

---

### Post by Officer Dibble on 2008-05-17
If I wanted to reinstall Leopard with a view to dual booting with Ubuntu, would I be better completely wiping the drive, or would the installation disk do this for me?

You guys are really helpful, thanks for your advice in anticipation. :)

---

### Post by neorou on 2008-05-17
Dibble,
If you have a Leopard DVD, I would definitely start with a complete zeroing of an HD using the Leopard DVD's disk utility. Then I would use disk utility to make my partitions first. I would also put the OS X HFS+ partition first - perhaps the Mach kernel looks for it in the partition serially as it boots after something goes wrong, and if the kernel encounters a non HFS+ partition (like the FAT32 that you had), it may not know what to do - thus the kernel panic.

I would use iREFit to manage the boot selection ([http://refit.sourceforge.net/](http://refit.sourceforge.net/)) along with Boot Camp. 
Before installing iREFit or UBUNTU, I would definitely run all the Mac updates.

If after all of this you are still having errors, I would locate the hardware test cd for you mac and run it just to see if there are any hardware issues. Make sure you do the extended test. You may want to do this anyway to rule out any potential hardware issues. The cd is not perfect, but as a long time mac user, I would rather have it than not.

Best of luck.

---

### Post by blurg on 2008-05-17
> **neorou said:**
>  I would also put the OS X HFS+ partition first - perhaps the Mach kernel looks for it in the partition serially as it boots after something goes wrong, and if the kernel encounters a non HFS+ partition (like the FAT32 that you had), it may not know what to do - thus the kernel panic.


The 200MB FAT32 partition is his EFI partition, leave it alone if you're keeping OS X, it is supposed to be there.

---

### Post by cyberdork33 on 2008-05-17
> **blurg said:**
> The 200MB FAT32 partition is his EFI partition, leave it alone if you're keeping OS X, it is supposed to be there.
yes and you should be able to reinstall into the existing OSX partition without a problem though it may disable rEFIt untill you reinstall it.

---

### Post by russo.mic on 2008-05-18
If your gonna reinstall OS X, I would partition from the get-go.

Create your partitons with the OS X Disk Utility during installation, and go from there.

---

### Post by Officer Dibble on 2008-05-18
You guys are megastars, many thanks to you all. =D>

I'm going to work my way through this again now - will let you know how I get on. :)

---

