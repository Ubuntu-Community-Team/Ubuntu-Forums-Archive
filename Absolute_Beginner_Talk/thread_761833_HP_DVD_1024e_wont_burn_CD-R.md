---
title: "HP DVD 1024e wont burn CD-R"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by loza on 2008-04-21
Hello

I am using Ubuntu 7.10 on  a toshiba laptop and have a HP DVD 1040e USB external Multi Format DVD writer which will burn DVD data backups with no problem at all.

However when I insert a CD-R to burn the application reports that the CD is no writeable. I have tried different brands of CD and different application to burn with and all report the CD is not writeable.

Does anyone know why this happens and if there is a configuration tweak I can do to get it working please?

thank you in advance

loza

P.s. It does work fine under MS windows xp.

---

### Post by loza on 2008-04-22
I wonder if it is something to do with the lightscribe??

My fstab has the following entries:

> proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=2f8f68a5-c640-4a50-9345-9d77e76889b1 / ext3 defaults,errors=remount-ro,noat
ime,data=writeback 0 1
# Entry for /dev/sda1 :
UUID=48FA7A574EF8CA42 /media/sda1 ntfs-3g defaults,locale=en_GB.UTF-8 0 1
# Entry for /dev/sda2 :
UUID=72e667b2-5e92-4a00-bb9e-5edce5e2f9d1 /boot ext3 defaults,errors=remount-ro,
noatime,data=writeback 0 0
# Entry for /dev/sda4 :
UUID=0f34da89-81fd-4d40-b423-d9bd74f2217f none swap sw 0 0
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0


---

### Post by jackflap on 2008-04-22
That's a tough one. Sounds like the driver that the kernel is using has a bug.

My initial response would be to download the latest 8.04 Release Candidate live cd ([http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)), boot into the live cd and test the drive to see if the newer kernel fixes the problem.

The problem is that since you'll have been booting using a live cd, you wont be able to test the cd-r drive since it'll be in use- I take it you dont have two cd-drives in the computer to run the test with.

Other solutions would be:
1) Install Hardy's kernel on your current installation manually. You'll need to download a bunch of packages, and install them. If the newer kernel breaks something though, you'll need to choose the old kernel from the grub menu when booting up, and go edit the configuration file to change the default kernel to the old one again. If you want to go with this, let me know and I'll give you further instructions.
2) Install Hardy over your current installation from scratch.

But the solution is in no way guaranteed to fix the problem. If I were a betting man, I'd say you're looking at 60% chances of it working.

Let me know what you want to do.

Alex

---

### Post by loza on 2008-04-22
Thanks Alex

I shall try a version 8.04 download as I will upgrade when it is released. I have an old internal cdrom I can boot from and try the external drive that way.

Thank you very much I shall let you know how I get on!

loza

---

### Post by jackflap on 2008-04-22
Mind you, the release candidate which I linked to before is pretty much release-ready at this point.

The release-candidate is the same thing as the final release, except they release it a week early so that there's enough testing to make sure no last-minute showstopper bugs arise, which almost never happens.

Also, if you install the RC now, just by continuing to install the regular updates, it will be exactly the same as the final release. If you're lazy to wait, I'd say it's safe to go ahead and test it now.

Alex

---

### Post by loza on 2008-04-24
Thanks Alex

I'm downloading RC8 now - I thought it might have appeared in my updates like 7.10 did when I was running 7.04, but it did not.

Anyway I shall keep you posted and once again thanks.

loza

---

### Post by loza on 2008-04-25
Hello

Just to let you know how I got on with this....

I installed RC8.04 and yes I can now burn CD-Rs sucessfully with the new updates applied!

The RC8 update went smoothly with now problems.

Thanks very much Alex

loza

---

