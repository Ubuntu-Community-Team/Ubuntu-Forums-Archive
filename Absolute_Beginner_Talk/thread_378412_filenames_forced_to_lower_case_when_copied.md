---
title: "filenames forced to lower case when copied"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by alpage2 on 2007-03-07
I am using Edubuntu 6.10, fully up to date with the automatic updates.

I am using cp to copy a bunch of files, mostly with upper case filenames, from a FAT32 partition (mounted at /mnt/win_d), to my home directory. After the copy command is executed, I find the destination files in my home directory have had all their filenames converted to lower case. How do I do a copy and preserve the upper case filenames?

I have read the cp manpage, but see nothing there about the case of filenames.

The command used was:

cp  /mnt/win_d/optimised/* /home/alan/optimised

Same thing happens when I use the dolphin file manager to copy the files across.

Thanks in anticipation
Alan

---

### Post by alpage2 on 2007-03-07
I have just discovered the source of the problem also involves WinXP, and possibly not the cp command...

The original files on WinXP are definitely upper case filenames, and are still upper case when uploaded to a linux webserver.

When copied into a FAT32 partition, Windows Explorer still displays the filenames as upper case.

After rebooting this dualboot machine into edubuntu and mounting the FAT32 partition, the filenames (which were upper case in Windows) appear to linux as lower case. Still lower case when copied to the home directory and still lowercase when uploaded to the linux webserver - that is clear because the links no longer work!

This is very confusing - are the files on the FAT32 partition upper or lowercase filenames? WinXP and edubuntu disagree!!!

Just to add to the confusion, there are a handful of files in this batch which have a mixture of upper and lower case filenames, and this mixture is preserved when the files are copied to FAT32 and thence to the linux partition - so WinXP and Linux agree on the mix of upper and lowercase characters, when there is a mixture, but see them differently if the filenames start out exclusively uppercase. Maybe this is some kind of character code problem?

Any clues as to how to resolve this, without having to manually rename all the files on my linux partition, one at a time, will be most welcome!

(If you are wondering why don't I just ftp the files with a windows ftp client - I have tried two, but for a while now, my windows ftp clients have been able to download files, but not upload - they were working normally up to about a month ago, when uploads suddenly started to fail - so I have been using gftp on linux instead - up 'til now!)

Alan

---

