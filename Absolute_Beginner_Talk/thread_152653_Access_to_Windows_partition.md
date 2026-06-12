---
title: "Access to Windows partition"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by flyingsolo on 2006-03-30
I know this is a recurring question but still am confused by other posts about this.  My old XP files are on one of two discs and I can 'see' it via System->Administration->Disks.  The NTFS partition is  /dev/hda2 and status is 'inaccessible'.  When I click on 'enable', nothing seems to happen.  Am I missing something here?  If & when I get access, I understand it will be 'read only' priveleges but can I use this to copy files to Ubuntu drive for backup or should I just boot windows and transfer with flash media?
Ongoing thanks for all the help.

---

### Post by Darkriser on 2006-03-30
well, i have ntfs partition and these steps work for me:

1) make sure your partition (let's take /dev/hda1, for example) is not mounted (sudo umount /dev/hda1)
3) sudo mkdir /media/any_name
2) sudo mount /dev/hda1 /media/any_name -t ntfs -o nls=utf8,umask=0222
or if you have fat partition use
sudo mount /dev/hda1 /media/any_name -t vfat -o iocharset=utf8,umask=000
3) cd /media/any_name -> and now you should be able to copy from that partition to ubuntu with no problem.

---

### Post by Princey on 2006-03-30
[QUOTE=flyingsolo]I know this is a recurring question but still am confused by other posts about this.  My old XP files are on one of two discs and I can 'see' it via System->Administration->Disks.  The NTFS partition is  /dev/hda2 and status is 'inaccessible'.  When I click on 'enable', nothing seems to happen.  Am I missing something here?  If & when I get access, I understand it will be 'read only' priveleges but can I use this to copy files to Ubuntu drive for backup or should I just boot windows and transfer with flash media?
Ongoing thanks for all the help.[/QUOTE]

Could you kindly take a look at this thread? [http://www.ubuntuforums.org/showthread.php?t=151587]("http://www.ubuntuforums.org/showthread.php?t=151587") It deals with the exact problem that you're talking about and there are several how to's step by step that you can follow. Hope this helps

---

### Post by meborc on 2006-03-30
how to automatically mount partitions during boot:
[https://wiki.ubuntu.com/AutomaticallyMountPartitions](https://wiki.ubuntu.com/AutomaticallyMountPartitions)

- a good read to all!

---

### Post by izmaelis on 2006-03-30
Open your terminal and enter command:
```
#sudo gedit /etc/fstab
```
Then add/edit a line:
```
/dev/hdaX       /media/hdaX     ntfs    nls=utf8,umask=0222 0   0
```
where /dev/hdaX is your NTFS partition and /media/hdaX is mountpoint. Save and exit from gedit. In terminal do:
```
#sudo mount -a
```
Now every user on your computer should be able to browse NTFS drive and copy files from there.

---

### Post by flyingsolo on 2006-03-30
Thanks--it works!  Most useful was meborc's link to the wiki re: AutomaticallyMountPartitions above.
By the way, as a newb, I'm amazed how long I can spend trolling the wiki or forums without answering my problem but posting the question ususally finds someone able to point the way--I think I may often have come across the answer on my own but not recognized it as the solution!
thanks again.

---

