---
title: "[SOLVED] Read-only Memory stick problem"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by bern1939 on 2008-01-08
I have a KINGSTON memory stick and wish to delete files from the .thrash folder
It will not allow me to do so saying "the file "Books.mdb cannot be deleted
because it is on a read-only disk.

What action can I take to correct the situation as they are taking up
unnessary space ?? And I do not have a write-protect switch on the stick.

Typing 'Mount' at the terminal shows the Kingston as follows:

/dev/sdb1 on /media/KINGSTON type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)


Thanks


Bernard

---

### Post by Mark_in_Hollywood on 2008-01-08
I had the same problem, sort of. You must delete as 

sudo

I'm no expert about this, it took a few attempts and finally I changed the file permissions (owership) and now I can delete ad lib.

---

### Post by philinux on 2008-01-08
You cant change the owner of the device
/dev/sdb1 

But you can do it to the mount point.
/media/KINGSTON

So a permanent fix would be

sudo chown -R yourusername /media/KINGSTON

---

### Post by bern1939 on 2008-01-08
So thank you both for your replies but no solution yet !

I did run  the sudo chown command and it appeared to be changing things but when I go to remove the directory & files contained therin I get the following:

[email]bernard@bernard-desktop:/media/KINGSTON/.Tras[/email]h-bernard/All Access Files$ sudo rm -r AccessTex

rm: cannot remove `AccessTex/PARAMETER.PDF': Read-only file system

rm: cannot remove `AccessTex/PARAMETER.PS': Read-only file system

rm: cannot remove `AccessTex/PARAMETER.TEX': Read-only file system

rm: cannot remove `AccessTex/PDFRULES.AUX': Read-only file system

Just to note  that the folder/files are in the ".Trash-bernard" folder -(a hidden folder) on the Kingston stick.

As you probably know  to unmount the Kingston one is  asked to empty the .Trash or not.
The only way I have of unmounting is to say 'No' ! And of course the offending folder&files then remain on the stick !

Any further ideas?

Thanks 
Bernard

---

### Post by bern1939 on 2008-01-08
Just remembered a way to get around this. I decided to **_format the stick_** having first made a backup of
all the folders/files on the disk.

Then I did the following and all is now clean again:

Mounted  the memory stick
Opened  a terminal and typed  'mount' to find out the partition where the stick was mounted
Unmount the stick from the desktop .....right-click & unmount
In the terminal, typed  - sudo mkdosfs -I /dev/sdb1 .... (or whatever is correct for your stick)
Remove the stick and plug it back in again.
The name of the memory stick may have changed but that's no problem.

Thanks again


Bernard

---

### Post by Mark_in_Hollywood on 2008-01-09
Please mark this thread solved.

---

