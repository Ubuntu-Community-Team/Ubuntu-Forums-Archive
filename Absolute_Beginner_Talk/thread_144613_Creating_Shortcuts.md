---
title: "Creating Shortcuts"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by th3gh05t on 2006-03-14
Hi, 

I have a Windows partition with files that I would like to use regularly. 

I have followed this guide --> [https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28windows%29](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28windows%29)

..to get the partition mounted each time I start up. 

I would like to place a shortcut to a particular folder on the Desktop.

Also, how do I make the files on the windows partition able to write? Right now, they are only read-only.

Thanks, th3gh05t

---

### Post by Brunellus on 2006-03-14
do NOT write to an NTFS partition from Linux unless you really enjoy irreparable filesystem corruption.

---

### Post by th3gh05t on 2006-03-14
[QUOTE=Brunellus]do NOT write to an NTFS partition from Linux unless you really enjoy irreparable filesystem corruption.[/QUOTE]

ok. well, i am glad that i know that now. i guess that is why diskmounter doesnt allow a user to write to thsoe files.


How would i create a shortcut on the desktop to a folder on the windows partition?

---

### Post by ajgreeny on 2006-03-14
I'm using kde so I'm not sure about gnome, but if you right click on the desktop do you get a menu that includes something like Create new > Link to location (URL) ?  If so, click on that and just browse to the /media/windows/folder that you want the link to (it also works for single files too).

---

### Post by dvarsam on 2006-03-16
I did the following to create a "shortcut" to a Windows FAT32 Partition's Folder & it did NOT work:

1. Right-click on the Desktop & select "Create Laucher..."

2. Under the Text Box named "Name" - give any name you like - e.g. "FAT32 Partition"

3. Under the Text Box named "Command" - give e.g. "cd /mnt/fat32_files/Linux - All Files/Ubuntu"

4. Under the Text Box named "Type", I experimented using: "Application". "Directory" & "Link".

Outcome:
NOTHING Works !!!

What am I doing wrong?

Thanks.

P.S.> I think that it is NOT possible to create a "shortcut" in Ubuntu, pointing to either a Windows NTFS or a FAT32 Partition!!! Am I right on this?

---

### Post by steve.horsley on 2006-03-16
Using gnome/nautilus you can make a shortcut by dragging and dropping between two nautilus windows with the middle mouse button - there is no other way that I know of.

You can do it in command line with the command:
**ln -s name-of-target name-of-link**
frinstance **ln -s /mnt/windows/windows/Profiles /home/steve/win-profiles**

---

### Post by DJ Scribblinni on 2006-03-16
dvarsam  
It is possible to create a shortcut.  This is what I did:  Right click on the desktop> Select Create Launcher> Type in any name you want (ei. My Documents)> then in the Command area type in: nautilus /media/hda1/Foldername
From there on, at least for me, it will open the folder on the harddrive.  I did have problems if there was a space in the folder names, so I put quotes around the file point : nautilus "/media/hda1/Documents and Settings/xxxx/My Documents"
That which pointed to my home folder within windows.
Just be sure to keep in mind where the hard drive is mounted...
Hope that helps you out.

---

### Post by dvarsam on 2006-03-16
Dear "Steve.horsley":

Thank you for your reply!!!

You are great!

_To tell you something funny_:

Right now, I just want to say this:

"Dam(*)n it!
 My mouse does NOT have a third button!
 ...and even worse, it is Microsoft Two-buttoned Mouse!!!"

Does anybody know of some other workaround for this?

Thanks.

---

### Post by dvarsam on 2006-03-16
Aaaaahhhh !!!!

It works !!!

Thanks "DJ Scribblinni"!

This is how you can create a "shortcut" to a Windows (NTFS or FAT32) Hard Drive Partition's Folder:

1. Right-click on the Desktop & select "Create Laucher..."

2. Under the Text Box named "Name" - give any name you like - e.g. "FAT32 Folder"

3. Under the Text Box named "Command" - give e.g. "nautilus "/mnt/whatever/your/path/is""

  Note:
  If the path includes spaces, you need to put the path between "<path>" (quotes).

4. Under the Text Box named "Type", leave it at: "Application".
    (since we use the program "nautilus" for this)

Take care.

Thank you ALL!!!

P.S. > For 1,5 month man I have been moving around all the way from the "root" to go to other Partitions....
You don't know how much time you have saved me now guys!!!
Thanks!!!

---

### Post by th3gh05t on 2006-03-17
[QUOTE=DJ Scribblinni]dvarsam  
It is possible to create a shortcut.  This is what I did:  Right click on the desktop> Select Create Launcher> Type in any name you want (ei. My Documents)> then in the Command area type in: nautilus /media/hda1/Foldername
From there on, at least for me, it will open the folder on the harddrive.  I did have problems if there was a space in the folder names, so I put quotes around the file point : nautilus "/media/hda1/Documents and Settings/xxxx/My Documents"
That which pointed to my home folder within windows.
Just be sure to keep in mind where the hard drive is mounted...
Hope that helps you out.[/QUOTE]

Hey dude, thanks for the help!

I used your method for creating the link. But it didn't seem to work when I put  nautilus "/media/hda1/Documents and Settings/xxxx/My Documents"

I realized this because you had changed the 'Type' of launcher to 'Link'.

If you guys just change the type of the launcher to 'Link', you can input where the directory is located.

th3gh05t

---

### Post by RRS on 2006-03-18
I can't remember for sure but I believe what I did was simply copy/past the drive from "computor" to "desktop" in Nautilous.

You can also right click on the desired folder to make a link and then right click on the desktop icon to rename it.

Unless you're already in terminal it seems a little quicker then the other methods. (I can't type worth a d**m)

---

### Post by kent41 on 2006-03-18
Hi

Is it possible to create a shortcut on your desktop to start a Web page ?
If so what would it look like.
Thanks

---

### Post by steve.horsley on 2006-03-18
[QUOTE=dvarsam]Dear "Steve.horsley":

Thank you for your reply!!!

You are great!
[/QUOTE]
<blush - thank you>
> 

 My mouse does NOT have a third button!
 ...and even worse, it is Microsoft Two-buttoned Mouse!!!"

Does anybody know of some other workaround for this?

Thanks.
Drag with **both** buttons then - this emulates the middle button. You can use a both-button click to emulate a middle-button click too, which tells firefox to open a link in a new tab. I think I'm going to wear my middle button out soon.

---

### Post by dvarsam on 2006-03-18
Dear "Steve Horsley",

you are an Ubuntu knowledge "bulldozer", man!

What I mean, is that you are an Ubuntu knowledge DATABASE - just yourself - man!!!

You are awesome,

Thanks!!!

---

### Post by beej101 on 2006-03-18
i've tried the one's that worked here and i just want know how do i get write permission to a shared FAT partition?  i see the lock icon beside every folder in my common partition and it is set to root as owner so i have to launch the file browser from root if i want to be able to have write access to my folders.  how do i change it so that whenever i launch the file browser and the shortcut in the desktop to my common partition that launches the file browser to have write access to my common folders even if im not root?  thanks!

---

### Post by steve.horsley on 2006-03-18
I think the problem is the umask in the file /etc/fstab (this file controls which partitions get mounted at boot, and sets the options). Here is my line for my FAT partition as an example:
```

/dev/hda9   /mnt/E     vfat    umask=0,iocharset=iso8859-15,codepage=850        0       0
```
Notice the umask of 0. After editing this file, you need to unmount and re-mount the partition to make the new setting work.

---

### Post by qpackard on 2006-04-02
What everyone but me seems to know is how do you know where to find the application to be launched? There are maybe several hundred folders. I'm not asking where the application is, I'm asking how am I supposed to _know_ where the application is, and then how am I supposed to know the name of the application? In windows the file is reliably downloaded to the same location (Desktop or any other chosen folder) and it almost always is named *.exe or *.zip.
Does ubunto/synaptic manager always download to a predictable folder?
Does the executable have a predictable name or suffix?

Just tired after spending a whole day trying to nail this one done, and I sure won't forget it once I learn it.

---

