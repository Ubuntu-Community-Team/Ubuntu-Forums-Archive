---
title: "i'm needing to automate a umount and partimage process when an icon is clicked. how?"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by ijason on 2007-11-13
hello. i'm in the last step of setting up a nearly automated restoration process for a computer illiterate friend. i've figured out how to use partimage to make a backup image of the partition to be restored, and the commands needed to erase the partition prior to the restoring. now i'm trying to set things up so she only has to click one or two icons to make it happen. i suspect i can do this fairly easily with a script? all the other script threads here relate to running a program, and i need to change directories, and umount a drive, etc etc.

basically the steps for process one is to umount a partition, remount it with ntfs read/write support, then wipe all its content and then umount it again.

the steps for process two is to use partimage to restore the partition to it's original state, and then mount the drive.

is a script the best way to do this? what is the syntax for putting mount/umount commands into a script? and how does a script handle the need for root password?

---

### Post by Nano Geek on 2007-11-14
> **ijason said:**
> hello. i'm in the last step of setting up a nearly automated restoration process for a computer illiterate friend. i've figured out how to use partimage to make a backup image of the partition to be restored, and the commands needed to erase the partition prior to the restoring. now i'm trying to set things up so she only has to click one or two icons to make it happen. i suspect i can do this fairly easily with a script? all the other script threads here relate to running a program, and i need to change directories, and umount a drive, etc etc.

basically the steps for process one is to umount a partition, remount it with ntfs read/write support, then wipe all its content and then umount it again.

the steps for process two is to use partimage to restore the partition to it's original state, and then mount the drive.

is a script the best way to do this? what is the syntax for putting mount/umount commands into a script? and how does a script handle the need for root password?In a Bash script, if you paste the commands one after the other, then they will be run in that order. To run Sudo commands in the GUI, just replace **sudo** with **gksudo**. That will pop up a window asking for the password.

This might help you if you are new to scripting.
[http://linuxreviews.org/beginner/Bash-Scripting-Introduction-HOWTO/en/index.html](http://linuxreviews.org/beginner/Bash-Scripting-Introduction-HOWTO/en/index.html)

---

