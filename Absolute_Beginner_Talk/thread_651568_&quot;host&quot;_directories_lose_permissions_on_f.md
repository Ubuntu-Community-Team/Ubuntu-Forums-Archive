---
title: "&quot;host&quot; directories lose permissions on filetranfer over sshfs"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by wankel on 2007-12-27
Dear community,

Having finished a fresh install of Kubuntu 7.10 on a new laptop, directories seem to lose their permissions.

This is my situation:
My wife got a new laptop. I installed Kubuntu on it, and made two users: one for her and one for me.
To save the hassle of customizing all of it, I am used to copy the contents of the users respective home directories in case of a fresh install.

In this case, I intended to copy files from her homedir on the old laptop to her new homedir, and from my work laptop to my homedir on her new laptop. I added both of us to the fuse group, made a temporary sshfs-dir in each homedir and mounted the respective homedirs to those folders.

This is the problem:
After copying a (smaller or larger) number of files, the mountpoint disappears, i.e, while copying I get the error that the source file does not exist, and on skipping the bunch of them, the mountpoint itself vanishes out of sight of the user.

On a commandline the directories are visible, but not accessible since the endpoint is not connected. Unmounting resolves the situation, but I am not yet done copying. I am using a wired network, with cables that are seemingly not broken.

This is how the directorylistings appear:
```
 linh@sandi:~$ ls -ltr
 total 0
 ?--------- ? ?    ?     ?                ? fuse
 linh@sandi:~$ cd fuse
 linh@sandi:~/fuse$ ls
 ls: .: Transport endpoint is not connected
 linh@sandi:~/fuse$ cd ..
 linh@sandi:~$ fusermount -u fuse
 linh@sandi:~$ cd fuse/
 linh@sandi:~/fuse$ ls -ltr
 total 0
 linh@sandi:
```

Any suggestion that does not involve just swapping my cables after all? :-)

PS, it will be some time later for me to check suggestions, last call for bed time :-). Thanks in advance!

---

### Post by blueridgedog on 2007-12-27
does ifconfig show any errors on either system's interface?

Can you simply sftp them?  Your method seems a bit more elaborate than needed for the task at hand.

---

### Post by wankel on 2007-12-28
Thanks for posting BRD,

Ifconfig did not show any problems, nor would my internet connection get (noticeably) interupted. In the light of a new day, swapping UTP and switch did not seem too much of a burden, and after that I did not encounter problems in copying, over sshfs, bit by it. 

At the .kde directory though, it still kept collapsing. Bye bye bad network theory, welcome SFTP.

It seems sshfs had a trouble enumerating all of the files in .kde. While using Konqeror for copying, it only listed some 5k files, good for 27MB. Using SFTP/fish on the other hand, it listed over 10k files, and over 80MB of data.

Though I could not find a solution for the sshfs problem, my task is solved. I will post a bug report for sshfs.

---

### Post by wankel on 2007-12-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/179041](https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/179041) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				launchpad: [https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/179041](https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/179041)

---

### Post by blueridgedog on 2007-12-28
Well done!  Your report is clear.

---

