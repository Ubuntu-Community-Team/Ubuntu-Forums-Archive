---
title: "How to upgrade Windows on a dual boot Linux system and get Ubuntu working again"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Khar136 on 2007-12-31
I have an older computer running Windows 2000 and Ubuntu 7.04. I decided to upgrade the Windows 2000 on it to Windows XP. If you do something similar, this email may help you.

My Windows was on partition 1 and my Linux on partition 3, with partitions 2 and 4 being swap partitions.

So I booted the XP installation CD, quick formatted partition 1, and installed Windows XP. Great!

When I booted the computer, it would always boot XP without asking. This is a known issue with Windows. So based on **[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)**
I did this:

- Booted with the Ubuntu live CD. I ran the partition editor and changed the flags for partition one to not be boot, and set the boot flag for partition 3. I then started a terminal session and ran:
  sudo grub
  find /boot/grub/stage1   (which said (ha0,2) in my case)
  root (hd0,2)
  setup (hd0)

I then rebooted. The Ubuntu grub boot menu now appeared, but there were two problems:
1) I could only boot Windows and it said it was Windows 2000 (but did boot)
2) If I picked an Ubuntu option, it would not boot saying "Can not mount selected partition".

So I pressed 'e' on a linux option in the boot menu and noticed that it was saying the root was (hda0,3). 3? So I changed that to 2 and was able to boot Ubuntu. I then opened a terminal window and edited the file /boot/grub/menu.lst (I type "cd /boot/grub" and then "ee menu.lst"). I changed the title for my windows installation and changed hda3 in the file to hda2.

Obviously installing Windows renames the partitions or something.

Ok, rebooted again. I could now select Ubuntu or Windows from the menu and both would boot. Yai

So I went into Ubuntu and started copying some files from Ubuntu back to Windows. Except it would not let me see the Windows hard drive anymore. No go! So after a lot more Googling (see [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)) I did this:

- Open fstab (in /etc/fstab) in a text editor (as a super user, I typed "ee fstab"). This shows the system what partitions to mount.
- Executed the command "ls /dev/disk/by-uuid -alh" in another terminal window and compared the two.
In my case it seemed that they matched except that Windows changed the UUID if the windows partition, so I also changed it in fstab to match. For each entry given by ls, there was now a matching one in fstab.

Rebooted Ubuntu again!

YES! Now I can see my windows drive again from Linux. All seems to work.

So hopefully this post will save some of you some Googling.

I don't know if there is a tool to check fstab and auto detect and fix it up for you or not and if I need to do anything else or not. Might be nice.

I am hoping that this post will help someone else, or if there is something else I should be doing, that someone would point it out! Thanks.

---

### Post by pt123 on 2007-12-31
good for you but why dont you mark this thread as solved.

---

