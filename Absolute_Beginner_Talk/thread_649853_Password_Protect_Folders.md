---
title: "Password Protect Folders"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-12-25
Is it possible to make a folder require a password to open it?

---

### Post by LinuxIsInnovation on 2007-12-25
You can block access to the folder:
Do this as root

> #chmod -r <folder-name>

---

### Post by SOULRiDER on 2007-12-25
Other users (except for root) cant view your home folder so theres really no need to password anything.

---

### Post by jordank on 2007-12-25
I realize that, but what if i only have one user?  I often just leave my computer open, but there are always some things that you don't want the public to see.
I'd just like to password protect one folder, as opposed to making a whole new user.

---

### Post by LinuxIsInnovation on 2007-12-25
What I posted above is what I am doing now. I have one user. Nautilus is launched **without **administrative privileges. So when you make a folder unreadable through the root, you cannot open it through any nautilus window, provided that other's do not know your root password.

---

### Post by jordank on 2007-12-25
okay, i've never really used nautilus, but how would i go about opening the folder, after typing that code?  Does nautilus prompt you for it when you try to open it? And further, would I have to remember my root password to open it?

---

### Post by LinuxIsInnovation on 2007-12-25
Well, when you will attempt to open it, it will simply display: The folder contents cannot be displayed.
To unlock it
> chmod +r <folder-name>

Let it be nautilus, or thunar or dolphin, none have admin privileges on startup :)

---

### Post by SOULRiDER on 2007-12-25
> **jordank said:**
> okay, i've never really used nautilus, but how would i go about opening the folder, after typing that code?  Does nautilus prompt you for it when you try to open it? And further, would I have to remember my root password to open it?

Nautilus is the app you use in Ubuntu to browse directories.

---

### Post by Capricori on 2007-12-25
Another option would be encryption, but this sounds like overkill for what you want to do, and I don't think you can encrypt whole folders, only files (with PGP encryption, that is)
Just thought I'd throw that in there :)

Regards, 
Capricori

---

### Post by csaga on 2007-12-27
When I started my system, with Feitsy automatically mount the NTFS Windows filesystem, which is in a separate drive. I have a folder in the NTFS drive and how can I obtain password protection privileges with a diferent  Ubuntu user?
Thanks for help!

---

### Post by peakshysteria on 2007-12-31
> **sayakb said:**
> You can block access to the folder:
Do this as root

Hmm, if the path is /home/nils/belkin and it is the belkin folder which is supposed tp be protected then: chmod -r /home/nils/belkin or...?

---

### Post by kellemes on 2007-12-31
> **jordank said:**
> I realize that, but what if i only have one user?  I often just leave my computer open, but there are always some things that you don't want the public to see.
I'd just like to password protect one folder, as opposed to making a whole new user.

If it's just to protect your data from people passing by your pc.. you may also simply hide the folder and/or password protect your screensaver.
Just a thought..

---

### Post by peakshysteria on 2007-12-31
> **kellemes said:**
> If it's just to protect your data from people passing by your pc.. you may also simply hide the folder and/or password protect your screensaver.
Just a thought..

So then, how do i hide or unhide a folder?

---

### Post by kellemes on 2007-12-31
> **peakshysteria said:**
> So then, how do i hide or unhide a folder?

If the foldername is "myfolder" you simply rename it to ".myfolder" 
It's the dot that does it.
In your filemanager (nautilus) you can choose to "show hidden files/folders" if you need to work with it.

---

### Post by conehead77 on 2007-12-31
> **peakshysteria said:**
> So then, how do i hide or unhide a folder?

Just put a dot in front of the folder and it disappears like /home/user/.hidden_folder/. You can hide/unhide in Nautilus by pressing ctrl-h.

If you want encrypting, take a look on truecrypt. You can encrypt folders and entire partitions with it.

---

### Post by peakshysteria on 2007-12-31
Thanks a million guys :) And just in time for the party :) I really love the Ubuntu forums. Have nice new years eve people.

---

