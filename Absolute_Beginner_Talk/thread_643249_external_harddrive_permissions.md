---
title: "external harddrive permissions"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by SCHWARTZMC on 2007-12-17
First off...I am a noob running feisty

I have looked through various posts on this issue. i haven't made any progress doing so...so i was hoping someone could help me.

I would like to figure out how to change the permissions on my external harddrive. I first used it on  a Windows XP machine, where I pulled all the data for the harddrive. I do know that the harddrive is NTFS format.

i read a post where someone recommended the terminal command:

id
df -h

i don't know what any of it means, but here is the output:

matt@dell:~$ id
uid=1000(matt) gid=1000(matt) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),1000(matt)
matt@dell:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             107G   50G   52G  50% /
varrun                502M  108K  501M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb            502M  144K  501M   1% /proc/bus/usb
udev                  502M  144K  501M   1% /dev
devshm                502M     0  502M   0% /dev/shm
/dev/sda3             193M   21M  163M  12% /boot
tmpfs                 502M   33M  469M   7% /lib/modules/2.6.20-16-generic/volatile
/dev/sdb1             466G   80G  386G  18% /media/OneTouch4

_____________________________________________

hopefully the info i've provided makes sense. any assistance would be greatly appreciated.

---

### Post by kernel tom on 2007-12-17
i would start here and let us know if you run any problems...

[http://www.linux-ntfs.org/](http://www.linux-ntfs.org/)

-kt

---

### Post by vanadium on 2007-12-17
You are running Feisty. Feisty did not yet include write support for ntfs disks. Gutsy does include it by default. However, you can easily and reliably install ntfs write support in Feisty as well. Unmount and disconnect the drive. Open a terminal and instal ntfsconfig:

sudo apt-get install ntfsconfig

After this, you will find an ntfs configuration utility in the Applications menu, with just two checkboxes, one to activate write support for internal drives and one for external drives. Just check the one for external drives. Then connect the drive and it should work.

Here, there is an extensive explanation with screenshots:

[http://www.howtoforge.com/ntfs_3g_ubuntu_feisty](http://www.howtoforge.com/ntfs_3g_ubuntu_feisty)

---

### Post by SCHWARTZMC on 2007-12-17
Thank you, vanadium! it didn't seem like it at first, but that worked.

one other issue I am having is that I can't seem to unmount the hard drive. when I right click the background of the drive and click 'unmount volume' it tells me:

Cannot unmount the volume 'OneTouch4'.
Details: Cannot remove directory

click 'OK'

'Cannot eject volume'

the same thing happens if i click 'Eject' on the desktop icon. Is this a problem? What kind of damage can be done be simply unplugging the drive? Is there a way to correct this?

thanks again for any help provided,

---

### Post by vanadium on 2007-12-18
This is indeed a bug in Feisty. Are you fully up to date with your system, because I would expect it to be solved by now. Somewhere on the net you can find a workaround:

"Can you guys please temporarily move away /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi, then reboot and check if it works then? If so, then bug 63090 would be the root cause. Thanks in advance!"

The menu will change from eject to unmount.

---

### Post by AustinMarton on 2008-01-22
Hi there,

I'm running Fiesty and having the exact same problem as SCHWARTZMC; My external hard drive is formatted NTFS and I cannot write to it, and it fails to unmount.

The answers to this tread seem to explain how to fix these problems, but I am wondering if it is worth bothering with NTFS at all? Since this is a brand new harddrive and I only have a few files on it, I could just reformat it to FAT32? 

I am very wary of Linux NTFS support as I lost the entire contents of my partition a few months back when messing with GParted.

Any opinions on prefered format? 

Also, where would I go to update my system in such a way that it would fix the unmounting issue? I've been putting off the 200mb download that the autoupdate thing wants to do, do I just have to bare that?

Thanks heaps for any help, and for the answers above which will temporarily fix my first problem!

---

