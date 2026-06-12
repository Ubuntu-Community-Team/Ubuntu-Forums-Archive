---
title: "evolution backup"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by cptjaben on 2008-01-01
i'm trying to backup my evolution mail by copying the .evolution folder in my home directory to a usb harddrive. When i attempt to transfer the folder it tells me a little bit after half way through giving me a message saying,  Error "Invalid parameters" while copying and then giving a certain file name. Also when I backup using file>backup in evolution I cannot extract the backed up archive without getting an error message. However on the partition that also has my home directory and the evolution folder i'm trying to copy, has no problems if i save it or copy the folder to somewhere else in that partition. for example i can copy the .evolution folder to my desktop without any problems. I have tried using sudo nautlius but receive the same problem. Anyone have any ideas? Thanks.

---

### Post by dcstar on 2008-01-02
> **cptjaben said:**
> i'm trying to backup my evolution mail by copying the .evolution folder in my home directory to a usb harddrive. When i attempt to transfer the folder it tells me a little bit after half way through giving me a message saying,  Error "Invalid parameters" while copying and then giving a certain file name. Also when I backup using file>backup in evolution I cannot extract the backed up archive without getting an error message. However on the partition that also has my home directory and the evolution folder i'm trying to copy, has no problems if i save it or copy the folder to somewhere else in that partition. for example i can copy the .evolution folder to my desktop without any problems. I have tried using sudo nautlius but receive the same problem. Anyone have any ideas? Thanks.

Two things, either you have an e-mail folder name containing an illegal character - "illegal" only when the various copy/archive commands try to use it and the script interprets it as part of the command and doesn't like it.

It could be **" ' - . / \** or anything else that scripts of filenames/paths use - it could be difficult to find it as these things can be quite subtle when you have been using them in a system that has been working correctly for a while.

The other thing may be the overall path/filename length is too long, for example here is a long path from my Evolution system:

/home/dc/.evolution/mail/local/Inbox.sbd/RFC.sbd/Internet Tigers.sbd/Previous years.sbd/2006.sbd/Goodies.ibex.index.data

If you have long names in your Evolution folder and sub-folders then you could hit a limit when copying to a filesystem that adds in extra path characters and overall it exceeds the 255 character limit of FAT32 or EXT2.

---

### Post by cptjaben on 2008-01-02
does anyone know what the best way to back this up would be, could i burn it to a cd?

---

### Post by Spin Doctor on 2008-01-31
Hi cptjaben,

I had a harddisk crash on my other ubuntu system so I got to take a look at this backingup evolution mail. 

First of all..the greatest news is that in the new Evolution 2.21, backup functionality is included with an easy user interface. This Evolution will ship with Hardy.

However, in earlier versions of Evolution, in order to make a backup of your complete Evolution mail, calender, tasks, and addressbook, and your settings, please do the following in your terminal:

```
gconftool-2 --shutdown
evolution --force-shutdown
``````
cd ~
tar -cvzf evolution-backup.tar.gz .evolution .gconf/apps/evolution .gnome2_private/Evolution
```This creates an archived tar-file of all the files need for the back, that you can save on a usbstick. 

To restore your backup, you simply unpack this tar-archive into your  homefolder```
cd ~
tar -xvf evolution-backup.tar.gz

```Shutdown gconftool-2 and evolution ```
gconftool-2 --shutdown
evolution --force-shutdown
``` and then start evolution to have your backup activated.

If you have a chance..verify you can restore your backup. Nice to be sure how it works when you do need to use it =)

 I am glad I stumbled upon this post from my Google search for my answer so hopefully this will help ya too. Goodnite from Sweden!

---

