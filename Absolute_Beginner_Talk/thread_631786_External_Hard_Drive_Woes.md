---
title: "External Hard Drive Woes"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by tonyr1988 on 2007-12-04
Ever since I got my external hard drive, I've been having some problems. I got this one:

[http://www.circuitcity.com/ssm/Seagate-500GB-FreeAgent-Desktop-Drive-305004FDA1E1/sem/rpsm/oid/172685/catOid/-12976/rpem/ccd/productDetail.do?linkid=j13774590k32998&affiliateid=k32998&mid=&=](http://www.circuitcity.com/ssm/Seagate-500GB-FreeAgent-Desktop-Drive-305004FDA1E1/sem/rpsm/oid/172685/catOid/-12976/rpem/ccd/productDetail.do?linkid=j13774590k32998&affiliateid=k32998&mid=&=)

I completely wiped it and it is one big ext3 partition. I have it mounted as /home. However, I frequently have problems with mounting it. About half of the time, when I turn on my computer, it will mount it as read-only. What would be causing this?

When it's mounted read-only, I get this error:

> tony@tony-desktop:~$ touch a
touch: cannot touch `a': Read-only file system

So, I try this:

> tony@tony-desktop:~$ sudo mount -o remount,rw /dev/sda1
[sudo] password for tony:
mount: block device /dev/sda1 is write-protected, mounting read-only

Most searching I did brought up problems with ntfs drives, which didn't help me a ton. What can I do?

---

### Post by tonyr1988 on 2007-12-04
bump - this is a pretty big problem. Today, everything was booted just fine (I could read and write from the drive) and, out of nowhere, it went read-only on me. I tried to save a .txt file, and it wouldn't let me, and I began to get the errors above.

---

### Post by mikeytag on 2007-12-04
Tony,
Are you using an /etc/fstab entry to mount the drive or are you letting automount mount it for you? Another idea is that there could possibly be a problem with the external drive, and whenever Linux encounters this problem it remounts the drive as read only so as to protect your data. You may want to try booting the cd that came with the drive and seeing if it has a diagnostic utility to check for bad sectors and such.

---

### Post by mikeytag on 2007-12-04
Just noticed that the drive is a Seagate, they are usually good about giving you a bootable SeaTools CD that you can then use to diagnose the drive.

---

### Post by tonyr1988 on 2007-12-05
I'm doing it through /etc/fstab. Does Linux have any hard drive diagnostic tools?

It didn't have a CD included with the HDD, however they have some programs on their website. I can try and see if they run under Wine or not.

---

### Post by tonyr1988 on 2007-12-05
It looks like the SeaTools CD only covers Internal drives. Is that correct? If so, do you know of any other bootable CDs that can do HDD diagnosis?

---

### Post by mikeytag on 2007-12-10
tonyr1988,
Sorry this is so much later, but I found this post online and it looks like this covers exactly what you are talking about.

[http://alienghic.livejournal.com/382903.html](http://alienghic.livejournal.com/382903.html)

My guess is that the drive actually isn't bad, but that it is spinning down and not recovering. The post says that if you use the eSATA connection the drive restarts correctly after being spun down. However, I am not quite sure what type of connection that is.

---

### Post by candtalan on 2007-12-10
It is beginning to look as if seagate (external) drives are bad news. Is this being picked up in a way which might warn others? I would be really peeved if I had bought one and it did not work with linux!

Even as things stand I am going to avoid buying any seagate product from now on, on principle!

---

### Post by psusi on 2007-12-10
There was an article yesterday on slashdot mentioning external seagate drives having broken power saving features that power them down and disconnect from the USB bus, which Linux sees as you unplugging the drive while it is mounted.

---

