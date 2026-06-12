---
title: "Mystery Folders--Recycled"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-11-14
I can't rest till I find the answer to little mysteries like this.  :-k  In my folder /home there is a folder named /Recycled.  I don't believe it was there originally after I installed Ubuntu 6.06, dual boot with Windows XP SP2.  It contains two files:  desktop.ini and INFO2.  Desktop.ini is a Windows system file.  It contains two lines of text:  [.ShellClassInfo] and
CLSID={(long number)}.  In Ubuntu I did a search in the main Windows directory for a file containing that text and found three, all in a different subfolder of C:\recycler, each subfolder representing individual users.  The CLSID number does represent the recycle bin in the registry.  I suspect that the folder /home/Recycled might have been installed by Windows after I installed a small utility to permit me to mount and access my Linux directories in Windows with drive letters.  The mystery is that I cannot find those desktop.ini files in the subfolders of C:\Recycler from Windows.  I have enabled viewing hidden folders and system folders, and I can find desktop.ini files in other folders.  Does anyone know what's going on here?  I apologize if this is more a question about Windows than Ubuntu.

Buck

---

### Post by bodhi.zazen on 2006-11-14
Looks like a windows thing to me, but how did it get there?

Talk about viruses !

---

### Post by mdsmedia on 2006-11-14
> **bodhi.zazen said:**
> Looks like a windows thing to me, but how did it get there?

Talk about viruses !I think I've got a similar thing in my home folder, but not at my machine at the moment. It may well be a windows thing, but not uncommon either.

---

### Post by podunk on 2006-11-14
i think I'd format the hard drive, just to be on the safe side. :-D

---

### Post by CatKiller on 2006-11-14
It's a Windows thing. As I understand it, when you use Windows to delete a file from a partition for the first time, it creates the Recycler directory. I don't know how the System Volume Information directories get created.

If you plan on doing things with this partition in Windows, and you'd like to (almost) never see these directories in Ubuntu, you should be able to create a file called .hidden and put the names of the files you don't want to see in it.

---

### Post by Buck2348 on 2006-11-14
A curious thing, though is that the folder is named "Recycled," not "recycler."  I read somewhere, but can't find it now, that Ubuntu under certain circumstances creates a folder in the root of a directory called "Recycled."  But that doesn't chime with what I have--a folder with a Windows system file in it.

---

### Post by CatKiller on 2006-11-14
It might depend on the version of Windows - mine was Win2K. I think I might have seen Recycled in earlier versions (?)

The folder that Ubuntu makes is most likely to be called .Trash.

---

### Post by Buck2348 on 2006-11-15
I got some information on this--there is a way to read the desktop.ini and info2 files in Windows directories, though I don't know how and why they hide them so thoroughly that you have to know a trick to see them.  "Recycled" is definitely a Windows folder, but I still don't know why it is named "Recycled" instead of "Recycler."  You are right that earlier versions are different.  I have an old laptop with Win XP, no service packs installed, and the folder in the root (C:) directory is "Recycled."

Thank you for your replies.

Buck

---

