---
title: "Delete Fiolders from memory stick"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by bern1939 on 2008-01-02
When I try to remove the folders on my KINGSTON memory stick I get:

bernard@bernard-desktop:/media/KINGSTON$ rm Downloads
rm: cannot remove `Downloads': Read-only file system

What is the correct command to use to delete the folder off the stick please.

Thanks


Bernard

---

### Post by rodo-&gt;dave on 2008-01-02
You know those sigs that say "if someone says do a rm -rf ... don't do it" well to remove the directory and all of the contents then you would have to either cd to the directory and rm all the files under it and then do a rmdir on Downloads or you could do this from your "bernard@bernard-desktop:/media/KINGSTON$" prompt:
rm -rf Downloads
but note that this will remove the Downloads directory and all files and subdirectories in it.
Please be careful with this command and make sure that you want to remove the directory and files listed!!!!

Another, safer way, is to use Nautilus and then RMC on the Directory and then select "Move to Trash"; the files will be put in the .trash directory on your USB drive which you can empty from the File menu.

You may have to SUDO it depending on permissions.

---

### Post by bern1939 on 2008-01-02
Many thanks but ..................

bernard@bernard-desktop:/media/KINGSTON$ rm -rf Envelopes
rm: cannot remove `Envelopes/Angela.doc': Read-only file system
rm: cannot remove `Envelopes/Ann Marie.doc': Read-only file system
rm: cannot remove `Envelopes/Bergin.doc': Read-only file system

etc. etc.

The read-only seems to stop the deletion.

?????

Bernard

---

### Post by Cavalryman on 2008-01-02
Many memory sticks have a tiny sliding switch which makes them "read only" so that they can't be accidentally erased. Is it possible that you accidentally engaged the switch?

---

### Post by antisocialist on 2008-01-02
type ```
sudo rm -rf dir/to/files -i
```

that means

**sudo** super user do, does something as root
**rm -rf** remove folder files and subdirectories
**dir/to/files** this is where the folder which you want to completely delete all its files, subdirectories, and the directory
**-i** simply asks for confirmation, it is a good idea to ALWAYS use this when using a command with rm in it, especially if -rf is also in the command

hope this helps :-p

---

### Post by bern1939 on 2008-01-02
Afraid not ..... got this stick last week and have transferred folders to it no problem....Ubuntu only.
I notice that all of the folders on the stick have a 'lock' emblem attached ??

How can I remove the read-only status I wonder?


Bernard

---

### Post by bern1939 on 2008-01-02
Just closed down the system and when I re-opened it the 'lock' emblems were not attached to the folders anymore.
The command rm -rf now works fine !!

Can't figure that one but it works.

Many thanks


Bernard

---

### Post by p_quarles on 2008-01-02
I had a similar issue a while back with a Kingston memory stick. There was something about the formatting that made it read-only on Linux, and to solve the problem I ended up having to reformat it. 

The easiest way to do that would be to install Gparted from the repositories, and then use that to format the disk. Choose FAT32 if you want cross-system (Windows, Linux, Mac) compatibility.

---

### Post by bern1939 on 2008-01-02
Thanks to all .... learned a lot here!


Bernard

---

