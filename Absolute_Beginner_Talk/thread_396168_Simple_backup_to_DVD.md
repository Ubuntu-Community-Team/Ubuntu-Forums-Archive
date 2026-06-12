---
title: "Simple backup to DVD"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by ushills on 2007-03-29
Hi

I have a problem with Simple backup; I have created a folder called backup on my desktop with the intention that backups will go into this folder and I can then burn them to DVD (I have given up trying to get permissions with UDF-packet writing).

The backup runs and when it has finished the folder becomes locked as all permissions are set to root.  Likewise each file is also set to root access only.

If I use chmod 777 and enable access then I have to then do this for each sub-folder and file.

How can I run a backup and place the folder onto my desktop and burn to DVD without having to jump though hoops with the terminal?

I need a quick reliable (automated) if possible method of backing up my home folder to DVD (or ideally DVD-RAM).

Ian

---

### Post by kpagpa on 2007-03-29
Hi Ian,

One method that might work is if you go to terminal and type:

gksudo nautilus

It will ask for your password to perform administrative tasks.  Once entered, a window opens with the file system, and you can work in that window as root so you can modify things as you like.  I don't know if this would include burning to DVD but you could try it.  Maybe there is a quicker method, in which case I hope that someone posts it.

Good luck!

Kevin

---

### Post by ushills on 2007-03-29
Will I have to do that everytime.

Why when I create the backup folder as a user and run the backup as that user does the outputted backup file have only root permissions.  Likewise my UDF DVD has only root permissions, I suppose I could add myself to the root group but don't want to do that for safety reasons.

I am still trying to understand the whole permissions things and how they are inherited.

---

### Post by kpagpa on 2007-03-29
Hi,

I don't really understand the whole permissions thing myself, so I can't really help.  I do find it to be a bit of a pain, but most of the time it isn't an issue as the documents I create don't have root permissions so I can change them as I like.  It's only when dealing with system files that it becomes an issue.

I suppose it makes sense to have root permissions on important things like backups.  I deleted some backups from my system yesterday and to do that, I had to use the procedure I outlined to you.

I guess you will have to do that every time you want to change files that have root permissions.

I found this article useful:

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

:)

---

### Post by ushills on 2007-03-29
Thanks that looks helpful, however, I am still confused as to why a folder that is within my Home folder i.e. Desktop inherits root permission.

I will try burning it to DVD one I am in as root.

---

### Post by kpagpa on 2007-03-29
Hi again!

I read this, and this might be the quickest way to do what you want to do:

[B]Drag & Drop Sudo

This is a trick from the [WWW] forums.

Create a launcher with the following command:

gksudo "gnome-open %u"

When you drag and drop any file on this launcher (it's useful to put it on the desktop or on a panel), it will be opened as root with its own associated application. This is helpful especially when you're editing config files owned by root, since they will be opened as read only by default with gedit, etc.[/B]

You can find this on [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by asimonelli on 2007-03-29
chmod has an option -R which applies the settings to the folder and all sub-folders and files.

chmod -R 777 <folder>

---

