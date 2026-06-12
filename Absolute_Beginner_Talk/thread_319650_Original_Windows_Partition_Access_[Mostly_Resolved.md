---
title: "Original Windows Partition Access [Mostly Resolved]"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by luckygerbils on 2006-12-16
Though I've read a lot of topics on dual-boot/ntfs partitions and access problems, I can't find any that seem to apply well to my problem.  After a difficult install process (I started trying to install Edgy, but it wouldn't work, so I went back to Dapper) I finally managed to get Ubuntu up and running, however, like most new users I can see, I can't get access to my old Windows files.  I've tried as many of the tutorials as possible, but after going through them, nothing seems to change.

However, unlike most of the other people having this problem, when I go to System/Administration/Disks and select my Windows partition, I can go into Change and see all of my Windows files there, but when I try to access this folder normally, no files are shown.  In addition, I am unable to start  Windows normally, I load to the Windows logo, then it fails.

The files on my Wndows partition aren't absolutely essential, I could stand to reformat it and start over if that's the only option, but I'd really like not to, or at least I'd like to back some up before formatting.

---

### Post by aysiu on 2006-12-16
Is this one of the tutorials you tried?
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

If not, try it. And if so, post the output of these three terminal commands, and we'll see if we can't help you get it working: ```
sudo fdisk -l
cat /etc/fstab
df -h
``` That's a lowercase *L* at the end of the first command, by the way--not an uppercase *i* or the number one.

---

### Post by luckygerbils on 2006-12-16
Oh, wow, I feel stupid.  I had tried that one before, but I think I used the text from the FAT32 partition section as well.  It worked this time. I guess I assumed the problem had to be more complex than that because of all the install problems I had.  It still doesn't look like windows will boot alongside, but as long as I can backup my files now, I'm fine with reformatting that partition.  Thanks.

---

