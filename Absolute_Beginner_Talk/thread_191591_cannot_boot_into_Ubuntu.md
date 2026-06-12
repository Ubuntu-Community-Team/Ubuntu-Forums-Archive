---
title: "cannot boot into Ubuntu"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by keith whitehouse on 2006-06-07
Hi there,

I was running Dapper Drake and following a guide to make a backup.tgz file. I went away to get tea and when I came back it had stopped with an error (tar error exit delayed from previous error). I checked in root to see if it had made a backup.tgz file but did not find one. I also checked in /home just in case it was there. I turned off the computer but when I try to start now I get an error.

"your session only lasted less than 10 seconds, if you have not logged out yourself, this could mean that there is some installation problem, or that you may be out of disc space".

I could be out of disc space as in the past when I have been trying to make this backup.tgz it has tried to copy all of my 10 partitions on C:. It could have done that this time, but I do not know.

When it boots now I am back into the Ubuntu screen where it asks for my name and password, but then it gives the previous error message. If I start in recovery mode I finish up with a dos prompt which is for root. Any help to get it going again would be appreciated or I will just have to start again, which would be a shame as I am pleased with how it was last time I saw it.

best regards keith

ps I am in Windows at the moment.

---

### Post by johnc4510 on 2006-06-07
When you get the prompt, try this:
sudo apt-get clean
This will remove .deb files from /var/cache/apt/archive
These were the original packages needed for installation.
It might give you enough room to boot into the system
Good luck

---

### Post by nalmeth on 2006-06-07
try logging into failsafe terminal session, and running this command:
(replace username with *your username*)
```
sudo chown username /home/username
```

---

### Post by linuchsan on 2006-06-07
run df -h to see what space you have on the mounted drives.

---

### Post by keith whitehouse on 2006-06-07
Hi linuchsan. I typed in df -h and it says that /dev/sdb1 is 9.7 g and that used is 9.4 g and that available is 0.

It looks as if the backup.tgz has completely filled up the Ubunto partition.

johnc4510. I ran sudo apt-get clean but it did not appear to give me any extra space when I rechecked the disc.

nalmoth. I did not run your suggestion as it does not appear to be password, it just seems like i HAVE OVERDONE THINGS SOMEWHAT.

can I somehow locate the Ubuntu partition and list what files are on there and delete the offending one. How would be very helpful

best regards keith

---

### Post by keith whitehouse on 2006-06-08
Hi Linuchsan,

after a good nights sleep I followed on where I left off, and that was to try and find the file backup.tgz. From the prompt I typed ls which gave me some places to search. I finally found it in /media, I am not sure how it got there but I deleted it and ran df -h and from 9.7 g size and 9.4 used and available 0, I now have 9,7 g size, 2.1 g used and 7.1 available. I booted into Ubuntu and got a pop up saying something about Gnome, but I stll clicked log in and bingo I am back into Ubuntu Dapper Drake.

Many thanks for the advice from you all

best regards keith.

ps I still have to find a way to either backup or to make a mirror image. I have had a look at all of the programs that are available but none of them seem to be intuitive

---

