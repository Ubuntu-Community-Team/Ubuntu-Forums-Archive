---
title: "permanant mount (pardon?)"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by manicmailman on 2008-04-10
i have a 'media' ntfs HD with all my music on it...
when i start ubuntu i have to go into 'computer' and mount the drive to my desktop every time... 
is there a way to permanently mount it?... (i realize the answer to that is "yes, yes there is"... so the real question is 'how?')

---

### Post by jcwmoore on 2008-04-10
[http://ubuntuforums.org/showthread.php?t=184605]("http://ubuntuforums.org/showthread.php?t=184605")

look here:popcorn:

---

### Post by ferdostar on 2008-04-10
> **manicmailman said:**
> i have a 'media' ntfs HD with all my music on it...
when i start ubuntu i have to go into 'computer' and mount the drive to my desktop every time... 
is there a way to permanently mount it?... (i realize the answer to that is "yes, yes there is"... so the real question is 'how?')

Just add the partition you want to be mounted automatically into the /etc/fstab file
To edit the file type in terminal
```
sudo gedit /etc/fstab
```
and add your HD

---

### Post by bumanie on 2008-04-10
I suggest you may have to edit /etc/fstab. You should be able to have that drive/partition mounted at boot. Please post the output of > cat /etc/fstab

---

### Post by timswait on 2008-04-11
I'm in the same situation, all my documents on a different drive to my OS so I want all my hard drives mounted at boot. I understand I have to edit the fstab file, but what is the line I have to add and where do I add it? Can someone post a sample file that's been edited so I can copy and paste?
Also as this seems a common issue has anyone thought of including in the original install an option to mount all hard drives at start up, or producing a program to edit the fstab file automatically. I'm a bit of a numpty with computers and I always get nervous when I have to edit files which are vital to making my computer work! Just a suggestion.

---

### Post by hyper_ch on 2008-04-11
[https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=MountNtfsOnBoot](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=MountNtfsOnBoot)

---

### Post by manicmailman on 2008-04-11
> **timswait said:**
> I'm in the same situation, all my documents on a different drive to my OS so I want all my hard drives mounted at boot. I understand I have to edit the fstab file, but what is the line I have to add and where do I add it? Can someone post a sample file that's been edited so I can copy and paste?
Also as this seems a common issue has anyone thought of including in the original install an option to mount all hard drives at start up, or producing a program to edit the fstab file automatically. I'm a bit of a numpty with computers and I always get nervous when I have to edit files which are vital to making my computer work! Just a suggestion.

yes im also wondering this... edit with gedit... understood... but whats the code to get the ID for the drive i want to mount?

---

### Post by bumanie on 2008-04-11
If you post the output of terminal command
> sudo gedit /etc/fstab someone will assist you with the editing.

---

### Post by timswait on 2008-04-12
I've got mine working using the code on the link hyper_ch gave. Didn't really understand what to do with the bit that said: > Two additional parameters are "shortname=mixed" and "user=user,group=group". The first will take care that all-caps short filenames show up in all-caps instead of in small characters. The second will take care that you are the owner of all files on the vfat partition, this will allow you to maintain file modification date/time when copying files to the FAT32 partition.
I tried adding the parameters in the middle of the line, but it didn't seem to work so I left them out and it worked OK.
I still think it would be a good idea for future versions of Ubuntu to come with the option of permanently mounting NTFS/FAT partitions automatically as it's something lots of people want and having to edit start up files is always a bit off-putting.

---

