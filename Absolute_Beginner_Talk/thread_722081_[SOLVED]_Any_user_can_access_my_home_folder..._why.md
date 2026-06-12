---
title: "[SOLVED] Any user can access my home folder... why?"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by snuffy on 2008-03-12
My mum has just noticed that my dad can access her home folder from his login.... this is bad news as she has all sorts of 'mum-stuff' that dad must not see! god knows what.

i thought that was the idea of linux and user accounts... security, to keep other users out of your stuff?

could it be anything to to do with having her home folder set up on another drive? do i need to set some user permissions or something on that folder?

cheers.
tim.

---

### Post by Sukarn on 2008-03-12
By default, all users have read permission to a user's home.

You can change the permission.

Right click on the home folder (as root or as the user to whom it belongs) and remove read privilidges for "Group" and "Others".

---

### Post by Circus-Killer on 2008-03-12
before you do remove the permissions, snoop around your mom's home folder. report back with some juicy stuff. :lolflag:

---

### Post by Sukarn on 2008-03-12
> **Circus-Killer said:**
> before you do remove the permissions, snoop around your mom's home folder. report back with some juicy stuff. :lolflag:

:lolflag::lolflag::lolflag:

:guitar:

---

### Post by tubasoldier on 2008-03-12
"mom stuff"

LOL. HIDE THE PORN!

---

### Post by marckie on 2008-03-12
> **tubasoldier said:**
> "mom stuff"

LOL. HIDE THE PORN!

Yeah... "Mom-Stuff!"
Hide the PORN and encrypt it to be sure... Or Just grow up... Hehehehe... LOL...

---

### Post by Arkenzor on 2008-03-12
> **Sukarn said:**
> By default, all users have read permission to a user's home.

That's entirely false (I think).

However, the problem may be with the fact that it's on an external drive. FAT32 and NTFS partitions, for example, do not have file permissions, and are mounted read/write for all users by default. In that case, you won't be able to change permissions from the right click -> Properties window (or maybe you will, be they'll be reset on the next reboot).



Si, if your mom's home folder is on an NTFS or FAT32 partition, the solution will be to edit your /etc/fstab file:
```
sudo gedit /etc/fstab
```
Locate the line corresponding to that partition, and add
```
umask=600,uid=<the account name>
```
to the mount options (which, if you didn't touch anything, will probably simply be "default").
Then reboot.

If you're not sure you're writing the right thing and don't want to struggle with syntax errors then post the contents of your fstab here.



If your whole /home tree is on a separate FAT or NTFS partition however, then you won't be able to do anything because these file systems do not allow separate permissions for different files. In that situation I'd suggest you redo your partitioning scheme.



And once again, if there's no FAT32 or NTFS partition involved then the problem is elsewhere, and none of these solutions will work.

---

### Post by Sukarn on 2008-03-12
> **Arkenzor said:**
> 
[QUOTE=Sukarn;4499678]
By default, all users have read permission to a user's home.

That's entirely false (I think).
[/QUOTE]

Nah, My dad's account can read the files in my account and vice-versa.

I find this quite useful when my dad's using my comp and I suddenly need to access some information in some file from my account. I can just open it as a read only file from his account instead of logging into my account from a graphical interface or doing a "su" into my account from a terminal window.

---

### Post by scramasax on 2008-03-12
> **Sukarn said:**
> Nah, My dad's account can read the files in my account and vice-versa.

I find this quite useful when my dad's using my comp and I suddenly need to access some information in some file from my account. I can just open it as a read only file from his account instead of logging into my account from a graphical interface or doing a "su" into my account from a terminal window.

Yeah, by default the permissions on that directory are set to 755.

That's not surprising really in that you have "Public" in there.  People couldn't get to "Public" if they couldn't access the directory above it.  It's the same on Mac OS X.

However, on OS X, most subdirectories inside your home area are set to 700.  By default you have:

Desktop 700
Documents 700
Downloads 700
Library 700
Movies 700
Music 700
Pictures 700
Public 755
Sites 755

What you might do is reset the permissions of the similar subdirectories in your users' home directories similarly.

Resetting home/mum to 700 would break access to her "Public" folder.  But resetting home/mum/Documents to 700 wouldn't.  You'd just have to tell her not to save anything DIRECTLY in her home area, but only in "Documents".

---

### Post by Sukarn on 2008-03-13
> **scramasax said:**
> Yeah, by default the permissions on that directory are set to 755.

That's not surprising really in that you have "Public" in there.  People couldn't get to "Public" if they couldn't access the directory above it.  It's the same on Mac OS X.

However, on OS X, most subdirectories inside your home area are set to 700.  By default you have:

Desktop 700
Documents 700
Downloads 700
Library 700
Movies 700
Music 700
Pictures 700
Public 755
Sites 755

What you might do is reset the permissions of the similar subdirectories in your users' home directories similarly.

Resetting home/mum to 700 would break access to her "Public" folder.  But resetting home/mum/Documents to 700 wouldn't.  You'd just have to tell her not to save anything DIRECTLY in her home area, but only in "Documents".

I don't think that we have a "Public" directory in Ubuntu. If you do want to share some files, I think it would be best to just put those files on a separate partition visible to everyone and common to everyone.

---

### Post by snuffy on 2008-03-13
Thanks for all your advice, 

Sukarn's first post did the trick according to mum.  

I didn't like to look in her home folder, i remember i showed her how to use azureus once and what did she download?  A Girls Guide to 21st Century Sex, a filthy documentary with internal cameras and all sorts! 

Cheers everyone.

Tim.

---

### Post by Oldsoldier2003 on 2008-03-13
> **Arkenzor said:**
> 
<snip>
Si, if your mom's home folder is on an NTFS or FAT32 partition, the solution will be to edit your /etc/fstab file:
<snip>

If the /home partition resides on fat32 or ntfs Ubuntu won't boot. So its a non issue :)

---

