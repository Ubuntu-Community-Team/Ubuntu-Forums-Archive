---
title: "When do mountpoints appear in &quot;Computer&quot; in Nautilius?"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by frafu on 2006-08-24
Hello, 

Could anybody please tell me what I have to do to make a partition appear under the "Computer" place in Nautilius? Do I have to mount it on a special mountpoint? 

I am assuming that "Computer" in Nautilius is the standard place where partitions should appear as a driveIcon, as is shows the boot partition and the cdrom!? Or am I wrong? 

Thanks in advance. 

frafu

---

### Post by dannyboy79 on 2006-08-24
First paste what appears when you enter "sudo fdisk -l" (no quotes) into a terminal. Once you do that I can help you further. We need to update your /etc/fstab file so that it automatically mounts partitions to folders when you turn on your computer. Otherwise if you just want to mount partitions to folders without it happening automatically you would first create a folder, navigate to where you want the folder created in a terminal and then "mkdir media" or whatever you want the folder named. Then you will want to chown it with this command  chown -R "enter your username here" "/name of folder" Example of username dan and a folder named media would be "sudo chown -R dan /media" (chown changes the owner of the folder) then do a chmod on it by typing "sudo chmod -R 755 /media. (chmod changes the permissions of the folder I believe) Now that folder is owned by you and everyone can read, write, and execute files from this location. Also, when you create a sub folder, it will have the same attributes. Now that the folder is there you will want to mount a partition to it, so if after you did sudo fdisk -l you were informed that you have a hard drive hda or hdb or hdc, you will also have been informed what partition number it is also, so to mount it you'll type in sudo mount /dev/hda1 /home/dan/media in my example. If this all doesn't help you all you have to do is type in mount linux partition in linux and you'll find your answer. Good luck!

---

### Post by frafu on 2006-08-24
Do I get you right: If I mount them using fstab-file at boot, they will automatically show up in Nautilius under "Computer", but if I mount them manually using the mount command in the terminal, their content will only be available as in a normal folder!? 

Doesn't the location of the mountpoint have any relevance?

---

### Post by aeiah on 2006-08-24
i believe they have to be mounted in /media for them to show up in computer

---

### Post by frafu on 2006-08-24
> **aeiah said:**
> i believe they have to be mounted in /media for them to show up in computer

You are right; it seems to me after trying that: when mounted on a mointpoint in /media, it appears in "Computer" and on the desktop; however, when mounted in /mnt it does not appear anywhere and one has to navigate to the mounted folder. 

By the way: I mounted the partition by inserting it in fstab. 

frafu

---

### Post by dannyboy79 on 2006-08-24
Computer within Nautilus is simply like when you click on My Computer within WINXP. It is simply going to show you the folders within your computer. Mountpoints are merely another name for a folder within Linux! The way Linux works is that you MOUNT a partition or a hard drives contents into a Folder or a mountpoint as you call it. Also, it's kind of frustrating trying to help you when I clearly asked that you post your sudo fdisk -l contents and you didn't, instead you asked another question. I can't help you if you don't help me help you! Here is a great website regarding how linux works as far as mounting filesystems etc. [http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html). Good luck but it appears as though you may  have already found your answer but if I were you I would read the website I have attached so you become more familar why it happens the way it does in linux.

---

### Post by frafu on 2006-08-24
@dannyboy79

First of all, thanks for your help, especially the part about chmod and chown. I did not post the output of fdisk -l, because I thought it would take us away from what I was asking. So I decided to ask another question in order to make my previous question more clear. Sorry for not pointing it out right away. 

An example of the MacOSX world: when inserting a new harddisk in a Mac, each formatted partition appears after formatting automatically in the folder /Volumes and on the desktop. So I was wondering whether there was a "standard" mountpoint in Ubuntu to mount a folder/partition in order to make it appear as a driveicon in Nautilius. (or something similar) 

I was not looking for the syntax about how to mount a partition. 

Sorry for the misunderstanding. 

frafum

---

### Post by sjxm9203 on 2007-03-21
Just to continue this conversation a little bit:

I have added a remote windows file system to my places by using the "connect to server" choice on the drop down places menu.  

The filesystem appears as an icon on my desktop and as a place in my file browser.

My question is:  Where does this directory actually live on my filesystem right now?  I would like to go to the command line and cd to it, but i cannot find it.  

Coming from a MAC background I am used to these things showing up in the /Volumes folder (as mentioned above).  Is there any equivalent in Ubuntu.

Also, I have tried making my own directory and running mount -t smbfs to make the directory connection myself, but I could not get the file permissions with the server to work.  That is why I have gone the GUI route to mount the remote directory.

Thanks.

---

