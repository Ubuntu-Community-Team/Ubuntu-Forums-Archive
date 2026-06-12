---
title: "MacBook Air3,1: Edit /etc/mtab"
date: 2012-02-20
forum: Apple Hardware Users
---

### Post by ryalho on 2012-02-20
Hello, this is my first time on the forums!

I own a MacBook Air and have managed to boot Ubuntu onto one of my partitions using UNetbootin. When trying to install Ubuntu I get to 15% complete in the progress bar when I get an error that reads:

> Failed to unmount partitions

The installer needs to commit changes to partition tables,
but cannot do so because partitions on the following could
not be unmounted.

/cdrom

Please close any applications using these mount points.

Would you like the installer to try to unmount these partitions again?

Now obviously the main culprit is the /cdrom. I do not have a /cdrom on the Mac thus this is practically an error in the Ubuntu install.

I go to Ubuntu documentation and find this:

> Note2: Instead of using 'workaround', an alternative is to modify the file /etc/mtab by erasing the line that specifies the partition where the cdrom is mounted. This way the kernel thinks thats the /cdrom is not mounted and will not show the advice when installing ubuntu. I think this procedure is less dangerous than the one in the previus note.

Ok, we need to modify the /etc/mtab, that seems easy enough. Well it's not. Apparently mtab is a status file that is kept from being edited in anyway. Resources online have shown that no one is really willing to say how to edit the mtab file because the cardinal rule is to never edit the file because it would muck up your system. 

So here is my question. How do I delete the line ***/dev/sda3/cdrom vfat*** from the file? (I am only assuming that this is the line to delete of course.)

---

### Post by ryalho on 2012-02-20
> su
[password]
gedit


Open from within the program. Installed perfectly.

---

