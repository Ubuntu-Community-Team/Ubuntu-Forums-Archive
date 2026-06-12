---
title: "[SOLVED] Relocate Folders to New Physical Device"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Gary Nored on 2007-11-10
I want to relocate the Documents, Pictures, Music, etc. folders to a different physical hard drive. I read the tutorial about relocating /home but it does not cover my situation (all hard drives partitioned as I want them, Ubuntu 7.1 installed and operating). I don't want to repartition anything ... I just want to make these folders (and/or /home as necessary) point to folders an the other hard drive. 

Many thanks for all your help, both past and present. I could never make the switch to Ubuntu without you!

Gary

---

### Post by bongobonga on 2007-11-10
You can mount an physical device into any directory that you want to. If for example you have a new physical device, and you want to have the home directory entirely on that device, you can simply mount the new device into the home directory.  First though rename the existing home directory and when you have the new device mounted, simply copy over the contents. 

The procedure to do this using a terminal is as follows:

Rename the existing home directory
```
 mv /home /home_backup
```

Create a new home directory
```
mkdir /home 
```

Mount the physical device into the home directory
```
 mount  /dev/hd?? /home 
```
Copy over the files from the old home directory
```
 cp -r /home_backup/ /home 
```

To get the physical device to be mounted into the home directory automatically at start-up, you will need to edit the file /etc/fstab

---

### Post by trak87 on 2007-11-10
You could move those folders, but a lot of applications (OpenOffice, etc.) may be counting on these locations right where they are, so the thing to do is to create symbolic links to the new drive/directories using the exact same folder names.

First, assuming your second hard drive is set up and formatted and a directory called /mystuff is on this second hard drive and you've given it your user name permissions, THEN do something like this:

```
cd 
mv Documents Pictures Music /mystuff
ln -s /mystuff/Documents
ln -s /mystuff/Pictures
ln -s /mystuff/Music

```

Now, do a *ls -l* and you'll see that you've created symbolic links with the same directory names that point to the actual folders on /mystuff. Now whenever OpenOffice wants to save or retrieve something at ~/Documents, it will actually be reading/writing to /mystuff on the other drive.

If you need help creating the directory or setting the correct ownership/permissions on the second drive, just ask.

---

### Post by Gary Nored on 2007-11-10
Links sound perfect; but when I try the mv command, it tells me that -s is not an option. Will the link command do as well?

TIA
Gary

---

### Post by mcduck on 2007-11-10
THe mv command was for moving your directories into the new drive. It doesn't need any '-s' option.

The ln -s commands create the links.

Of course you need to run them both. Just moving the directories won't make links for you, and you can't make the links if the directories are not on the new drive ;)

edit: you need to run each command separately. so copy/paste those commands one line at time..

---

### Post by Gary Nored on 2007-11-10
Cancel, cancel. Sorry about that. When I did the first ln I must have done something wrong because when I attempted to go to the Documents directory, i got an error message about too many levels. I tried apropos for a command so that I could fix that. Cleanlinks looked really good. I ran it, and now all the folders in the left panel of the browser are gone. 

Sigh ... it was only to be a convenience anyway. I can easily access and use the data drive as it is. 

Thanks for the help. It's only my ignorance that makes me crazy :)

Gary

---

