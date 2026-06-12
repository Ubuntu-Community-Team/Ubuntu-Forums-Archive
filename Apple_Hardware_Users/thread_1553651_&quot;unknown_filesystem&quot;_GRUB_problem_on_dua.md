---
title: "&quot;unknown filesystem&quot; GRUB problem on dual-booting MacBook Pro"
date: 2010-08-15
forum: Apple Hardware Users
---

### Post by Halsnalle on 2010-08-15
I've got an old MacBook Pro on which I successfully installed Mac OS X and Ubuntu to dual boot, following [these instructions]("http://ubuntuforums.org/showpost.php?p=9347165&postcount=70").

After that, I shrunk the Mac OS X partition using Gparted, [as suggested in this thread]("http://ubuntuforums.org/showthread.php?t=1495665"), in order to get a new partition for files shared between Mac OS X and Ubuntu.

That went well, but now I can't boot Ubuntu: After selecting Ubuntu in rEFIt after startup, I get an error saying:

> error: unknown filesystem
grub rescue


After some googling, I've guessed that I need to reinstall Grub. I've tried following [these instructions]("http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-unknown-filesystem-grub-rescue-781125/#post3846939") ("second way").

...but "fdisk -l" only shows the first four partitions (sda1-4), although I have six partitions. Anyway, I thought I should install Grub at /dev/sda4/ (but perhaps that's wrong?) in order to avoid the partition map overlap problems outlined in the post linked above, so I modified the commands like this:

> sudo mount -t ntfs /dev/sda4 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda4


But when I run that last line, I get the following warning:

> "warn: Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
warn: Embedding is not possible. GRUB can only be installed in this setup by using blocklists. However, blocklists are UNRELIABLE and its use is discouraged."


So I guess that's not the right thing to do either.

[A reply in this thread]("http://ubuntuforums.org/showpost.php?p=9439632&postcount=72") suggests that having a separate partition for Grub is unnecessary. Should I simply delete the GRUB partition and reinstall it to the Ubuntu partition? If so, how do I do that...?

This is how my disk is partitioned according to Gparted:

/dev/sda1   fat32   EFI 200.00 MB
/dev/sda2   hfs+   Mac OS X   34.18 GB
/dev/sda3   hfs+   shared partition for files   232.57 GB
unallocated   128.00 MB
/dev/sda4   ntfs   grub   509.88 MB
/dev/sda5   ext4   Ubuntu   27.94 GB
/dev/sda6   linux-swap   2.58 GB

Help is much appreciated!

---

