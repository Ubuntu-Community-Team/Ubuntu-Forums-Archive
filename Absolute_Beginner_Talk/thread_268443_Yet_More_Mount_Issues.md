---
title: "Yet More Mount Issues"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by JesusOnEez on 2006-09-30
OK, I know there are a plethora of mount issues and answers, but I've tried a load and am getting no joy and need some help.  Note that this is the first time I've installed any Linux distro, but am fairly techy when it comes to Windows itself.  

Generally, I was impressed by how much worked on install.  Ubuntu picked up an IP from my DSL router giving me instant internet access, and also, connecting to my Windows 2003 server was a breeze, and I have full access to that...impressive.

Firstly, my setup is one 160Gb SATA HDD.  I have an 80Gb NTFS partition that Linux sees as SDA1, and a 50Gb NTFS partition that Linux sees as SDA5.  Ubuntu is on the remainder of the space, SDA3.  

Discs Manager shows that the two NTFS partitions are located;

/tmp/disks-conf-sda1
/tmp/disks-conf-sda5

This means nothing to me as a linux noober but suggests I should be able to get into them.  All my media files are on sda5.

Nautilus shows the two NTFS partitions, but when I double click on them, I get the following;

You do not have the permissions necessary to view the contents of "disks-conf-sda5".

I am logged in as the user created by Ubuntu at install time.  I understand this to not be the "super" user...

I have tried the following at the Terminal;

sudo mkdir /media/windows
sudo mount /dev/sda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

I have no idea what any of this means.  It results in the following;

mount: /dev/sda1 already mounted or /media/windows/ busy
mount: according to mtab, /dev/sda1 is mounted on /tmp/disks-conf-sda1

The above was a suggestion linked to from these forums for someone with a similar issue, only his were listed as hda partitions.  I believe hda and sda to be the difference between IDE and SATA drives respectively.  What this seems to be telling me from my Windows bias brain, is that the volumes are already mounted, but I'm not allowed to access them.

Any help much appreciated.

---

### Post by aysiu on 2006-09-30
It sounds as if the partition's already mounted but in such a way as to make it unreadable. This is a stupid Ubuntu thing that I hope the developers fix for the next release.

Knoppix and Mepis allow you to open and read any partition with a single click.

In Ubuntu, you have to manually edit your /etc/fstab file.
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by JesusOnEez on 2006-09-30
Thanks for the link...

What's a Knoppix and/or a Mepis?

I'll have a look at the link and see what's the wat and get back to you.

---

### Post by JesusOnEez on 2006-09-30
That link 99% worked so thank you.

I can now get at my NTFS partitions via Disks Manager's browse facility.  They no longer show up in Nautilus, whereas they did before (when I couldn't get into them).  Any idea's how to get them to show up in Nautilus again?

---

### Post by aysiu on 2006-09-30
Knoppix and Mepis are other versions of Linux than Ubuntu.

I love Ubuntu for its community and documentation, but it's still got some catching up to do, software-wise.

---

### Post by aysiu on 2006-09-30
> **JesusOnEez said:**
> That link 99% worked so thank you.

I can now get at my NTFS partitions via Disks Manager's browse facility.  They no longer show up in Nautilus, whereas they did before (when I couldn't get into them).  Any idea's how to get them to show up in Nautilus again?
Well, in that HowTo I had you mount them to a static directory. I do this because I've sometimes had people have issues with FAT32 in particular having weird permissions when mounted in the /media directory.

If you mount the partition in the /media directory, it'll show up on your desktop. Alternatively, you can keep it mounted at /windows and then link it to your desktop: ```
ln -s /windows ~/Desktop/windows
``` You can also bookmark the location in Nautilus.

---

### Post by JesusOnEez on 2006-09-30
OK, I'll have a play later...going out to lunch now.

Thanks again.

---

