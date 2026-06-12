---
title: "/home on its own partition?"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by symbiont7 on 2006-07-02
Alright, I'm still investigating things, haven't installed anything yet, just running from the LiveCD.

Question...
In Win XP I have the "My Documents" folder mapped to its own partition, that way when I reinstall the OS I don't have to worry about my files (pics, vids, music, word processing, etc.) getting messed up or lost. It also makes backing up a breeze.

So, is the /home directory in Linux basically the same thing as the My Documents in XP? I mean, is that where all the user's files will go (not apps, settings,etc.)? And I assume I could put the /home directory on its own partition?

I know I need to partition during/before the actual install of Ubuntu, but do I specify the /home location at that time, or change it after the OS is installed like I do in WinXP?

As always, thanks for the help!

---

### Post by mips on 2006-07-02
Yes, home is basically the equivalent of Documents & Settings folder in windows.

Yes you can install /home to it's own partition and it is the smart thing to do. This way you can re-install play around with the OS partition and not worry about borking your data partition.

The partitioner on the livecd did not work for me and actually wiped my fat32 data partition (luckily I had backups), this was not user error and I can replicate the problem at will. The alternate cd worked much better for me. When you get to the partioner you simply create your partitions and select the mount points from the options (think you press enter or space on them, somebody correct me).

I have gone the route of mirroring my data across two drives on two equal size partitions, one fat32 and one XFS. I used to get errors with ext3 filesystem on my data partition for some odd reason, still use it for my / partition though.

---

### Post by someusernoob on 2006-07-02
And even better then that.

In your /home folder there are .hidden folders containing the configuration files of programs.

So for example i have Thunderbird and Xchat installed. They both have a .hidden folder in the /home dir.

When i decide to do a fresh install of Ubuntu, the only thing i have to do is install these programs, and run them, they have kept there configuration. A fresh install only costs about ~30 minutes, and you have only to configure everything once!

That is really brilliant. (And if you dont want the configurations you can off course delete those folders)

---

During the installation choose "Manual edit partition lay-out", create the needed partitions (/ [root], /swap, /home) and in the next screen you can set the mount points to them. When you do a reinstall, do the same, but do not format the /home directory.

---

