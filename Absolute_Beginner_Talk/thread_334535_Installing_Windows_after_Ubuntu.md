---
title: "Installing Windows after Ubuntu"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by uthpalawe on 2007-01-09
Recently I had a virus attack on by windows OS and I am going to reinstall windows as it does  not boot up but just keep on rebooting. I read some articles on this forum but I am not clear about one fact. After I execute setup(hd0) will my machine function as usual or should do something more. 

Thanks.

---

### Post by deadgobby on 2007-01-09
What type of virus?

---

### Post by vf514 on 2007-01-09
/dev/hd0 is your master boot record, and it is unlikely that this is where you intend to actually reinstall your operating system. Currently, Windows resides on a current partition on your computer, say /dev/hd1, which is the first partition that will be listed. In this case, Windows should be reinstalled with the first listed partition.

To determine the partition Ubuntu resides on, examine /etc/fstab and look for the location of your root (/) file system. You will need this information later.

Identifying the partition on which Windows is installed should not be difficult since the default file system used by Ubuntu (ext3) is recognizable; and thus you should reinstall Windows on the *recognized* partition, assuming there is only one installation of Windows on your computer. To do so, reformat the partition recognized by Windows Setup and reinstall your operating system on it.

Unfortunately, Ubuntu will be temporarily inaccessible after the reinstallation as Windows will automatically overwrite the master boot record with its own bootloader. To restore grub, you will need to chroot into your Ubuntu installation using the live CD, or a rescue CD if you are running a version of Ubuntu lower then 6.06. To do so, first boot your computer from the live/rescue CD and open a terminal. Now, create a directory (for example, /mnt/ubuntu) and cd into it. Issue:

$ sudo mount /dev/<ubuntu_partition> .

And now, chroot into the mounted file system:

$ sudo chroot . /bin/bash
$ sudo source /etc/profile

Finally, run grub-install:

$ sudo grub-install /dev/hda

Subsequently, reboot. Your system should now boot normally.

I recommend that you use the Firefox web browser and install anti-virus software on Windows, such as Avast. Doing so has kept my installation very secure.

**Edit:** First, see the post below this one.

---

### Post by Sef on 2007-01-09
[Recovering Ubuntu after Installing Windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

