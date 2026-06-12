---
title: "Newly created folder instantly locked"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by svdb on 2007-10-23
Hi all,

I couldn't find this topic on the forum.
I have ext2 drives sitting in a NAS and mounted using cifs.
My fstab looks like this:
```
//192.x.x.x/Backup /media/nasBackup cifs rw,user=***,password=***,uid=1000,gid=1000 0 0
```
When I log in using my regular user account and create a folder on my cifs mount using Nautilus, the folder instantly gets locked with user "1029" as owner.

Why am I not the owner of the folder "I" create?

How can I change this default behaviour?

Thanks.

Edit: When I copy/paste a file to my cifs mount, same result, the owner is "1029" but not me.

---

### Post by svdb on 2007-10-23
Anyone?

---

### Post by NilsE on 2007-10-23
I assume from your post old folders stay in your ownership with no problem. Correct?

Now, the only thing that jumps out at me is that if you create the new folder or file while you are acting as root (sudo or gksudo) then no matter where you place them they are owned by root.

If it is not that I have nothing else coming to mind right now.  If I get any brainstorms on the drive home I will post it.

---

### Post by svdb on 2007-10-23
Thanks Nilse,

I'm not root at the moment I create a new folder, only regular user account.
If I use SUDO then of course I can do what I want.
I could also use chmod, but I would like the ownership to be by default the user who created the file/folder.

I wonder if this happens because of the mapping options in fstab.
I looked at the manual, and tried different options... with the same result.

When I drag/drop a folder containing 10 files, from my home disk (owner of folder and files is me, not root) to my cifs mounted volume, the folder gets created, only one file is copied to it and the 9 remaining files spawn "access denied" errors.
If this was Windows, I'd say its a bug.

---

### Post by svdb on 2007-10-24
anyone?

---

### Post by NilsE on 2007-10-24
This is a shot in the dark but try replacing the section in your fstab with this starting at the cifs. I assume the user= and password= is required so you will need to enter them.

cifs  auto,user=***,password=***,sync,exec,uid=1000,gid=1000,umask=007 0 0

Also try it without the user=

cifs  auto,user,password=***,sync,exec,uid=1000,gid=1000,umask=007 0 0

---

### Post by svdb on 2007-10-24
Thanks Nilse,
I just tried both suggestions, rebooted each time, without success...
Owner of newly created folders and files is "1036", but still not me (stef).
I just wish all this cmd line stuff wasn't needed. It's getting annoying having to use chmod every two minutes. ](*,)
Thanks anyway.

---

### Post by tis_but_a_scratch on 2007-10-28
I just figured this out myself, if you add 'noperm'  to your parameters it should work.
ie it would be //192.x.x.x/Backup /media/nasBackup cifs rw,user=***,password=***,uid=1000,gid=1000,noperm 0 0

---

### Post by svdb on 2007-11-05
Ah, I'll have to try that ASAP! Thanks.

---

### Post by svdb on 2007-11-05
I just tested the noperm option and it seems to be working for newly created files and folders.

Some of the existing files and folders still have the same problem, but they were created when running Windows and accessing the NAS with samba. Not a big deal. They're not a majority of my files & folders.

Many thanks to this_but_a_scratch :)

---

