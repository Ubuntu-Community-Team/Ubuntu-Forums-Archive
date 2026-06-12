---
title: "Can't copy files onto different drives"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by kickstart on 2007-07-19
G'day,

I can't seem to copy files from my home drive (internal 500gb hard drive) to either my 250gb external usb drive or my 80gb external usb drive. When i try to copy a file to the drive this error occurs:

"Error copying to /media/250/Backup" "You do not have permissions to write to this folder"

When i try and change the permissions by right clicking on the drive on the desktop, and going properties --> permissions. I have no option to change the permission, all the boxes are unclickable etc

any ideas?

Cheers

---

### Post by lisati on 2007-07-19
[http://ubuntuforums.org/showthread.php?t=504381](http://ubuntuforums.org/showthread.php?t=504381) might help - external drives often need the same kind of help as NTFS file systems

---

### Post by kickstart on 2007-07-19
Thanks, it installed ok. And i set it to 'enable write support for external drives'  but now when i go to past something into the drive nothing happens, i just get a small box in the right hand lower corner that has the filename in a text box type thing, if i press enter it just goes away, the files do not transfer, if i click on the text, it appears to be editable. any ideas from here?

much appreciated.

---

### Post by Nevis on 2007-07-19
I had this problem myself. In my case the external drive was owned by root and users other than root had only read permission. If I recall correctly I took ownership using the chown command then changed the permissions with the chmod command. (use sudo)

This may not have been the right way to do it (I'm a relative Ubuntu newcomer) so hopefully someone wiser correct me if I'm wrong. At any rate it solved the problem for me.

---

### Post by kickstart on 2007-07-19
haha you may be new but i dont even know what the 'chown' and 'chmod' commands do:P

if anyone can help me clarify and fix my problem that'd be great

---

### Post by Nevis on 2007-07-19
lol, I hear you. :-)
But don't give up too soon, I didn't really understand them either until I researched it. Basically the folder has an owner, in this case likely 'root'. It also has read, write and execute permissions assigned for user, group, and others. User is the owner and since you're not root you're likely considered 'others'. I'd bet the permissions for 'others' is set to read only, thus you have no permission to write to the folder. 

Therefore, what you need to do is take ownership of the folder using the 'chown' command which should also give you write permission as the owner. If others need access to the drive you'll have to edit the permissions using the 'chmod' command.

Check out the links below for a description of the commands and some examples;

[http://en.wikipedia.org/wiki/Chown]("http://en.wikipedia.org/wiki/Chown")
[http://en.wikipedia.org/wiki/Chmod]("http://en.wikipedia.org/wiki/Chmod")

Good luck!

---

### Post by kickstart on 2007-07-19
Thanks Nevis, but i still have problems lol

After reading the wiki on Chown, i cannot take ownership of the drive (name: 250) my username is warwick btw, just so you understand what im writing.
I write this:

chown warwick /media/250
and i get this
Chown: changing ownership of '/media/250' : Read-only file system

so if i try this:
chown warwick /media                (to gain access to the media section)
i get:
chown : changing ownership of '/media' : Operatin not permitted

any further ideas?

thanks.

---

### Post by Nevis on 2007-07-19
As I said I'm new as well and we're getting into uncharted waters for me. :-)

However, it seems to me that the drive was mounted as read only. Typing
```
mount
```
in terminal should list all the drives and their mount options. This drive should be listed as '/dev/sda1 (or /dev/sda2) on /media/250' and you may see options near the end of this line in brackets. If it says (ro) the drive was mounted as read only, if it says (rw) the drive is mounted as read/write.

What you could do then is unmount the drive, then remount it specifying the options you want. You would also then have to edit your fstab file so that automount worked properly as well.

Here is the wiki page for the mount command;
[http://en.wikipedia.org/wiki/Mount_%28Unix%29]("http://en.wikipedia.org/wiki/Mount_%28Unix%29")

I know there's lot's of expertise on this forum and I'm hoping someone else will jump in here and share their wisdom!

---

### Post by Nevis on 2007-07-19
Also please check this [thread]("http://ubuntuforums.org/showthread.php?t=504495") as it's directly relevant! :-)

---

