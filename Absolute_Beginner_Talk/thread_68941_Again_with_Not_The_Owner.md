---
title: "Again with Not The Owner"
date: 2005-09-24
forum: Absolute Beginner Talk
---

### Post by sonyack on 2005-09-24
OK, apparently installed RealPlayer, launcher in applications > sound & video, all kinds of files in its folder.  But it doesn't launch.  Its folder has a lock symbol on it and I can't change permissions because I am "not the owner so [I] can't change permissions."

This happens a lot.  Anything I copy from a cd, e.g., gets a lock and I have to change permissions on the property sheet just to move it or delete it.

Anyway, what can I do about this, and how can I get this RealPlayer to work?

---

### Post by FLeiXiuS on 2005-09-24
Login as sudo then you'll beable to change the permissions. 

If your doing it in nautilus, then open a terminal and type:

$ gksudo nautilus 

That'll give you nautilus under root so you can change the permissions in the GUI.

---

### Post by mlomker on 2005-09-24
> This happens a lot.  Anything I copy from a cd, e.g., gets a lock and I have to change permissions on the property sheet just to move it or delete it.


That's probably because your CD is being mounted as root, which is the default.  I have a general [post](http://http://ubuntuforums.org/showpost.php?p=355988&postcount=8) about mounting with user permissions.  You'd have to substitute in the names of your mount point and the name of your cdrom.

Mine looks like this:

```

/dev/hdc        /media/hdc      auto     defaults,users,noauto   0       2

```

---

### Post by sonyack on 2005-09-24
OK, guys, thanks.  But I only know enough to get myself into trouble -- getting out of it  is "doh!"


So "log in as sudo and then you'll be able to change permissions" doesn't mean a lot to me.  I of course have used sudo in the terminal for installing FlashPlayer and I used it to get this RealPlayer bin to work, but using the terminal to change permissions is unlearned, if that is where I am to log in.  Is there a tutorial on this subject?  

Re:  files copied from cd locked -- right now I can just right click and change perms on the prop sheet.  Getting the os to stop locking copied files is down the road, as I just don't have the skills as yet.  I can see it's gonna be a long road <sigh>.

---

### Post by mlomker on 2005-09-25
> 
So "log in as sudo and then you'll be able to change permissions" doesn't mean a lot to me.  I of 

The **gksudo** part of that command opens nautilus as if you were root (the superuser with full permissions).

---

### Post by sonyack on 2005-09-25
sudo chown system_username /location_of_files_or_folders

Thanks, I'll try that one.  The command up above is what I found in the Unofficial guide, tried using it in a terminal, but it doesn't work:  when I type what I figure it should look like [sudo chown system_sonyack /home/sonyack/RealPlayer] terminal says "invalid user."

Oy.  Using the gksudo nautilus command in a terminal brings up a window that displays a folder labled Desktop, which is empty, and two text files.  The button in the lower left corner gives you / and Root.  So I nav in / to Home and find the RealPlayer folder.  On its prop sheet, I used the check boxes to check all of them and now the lock is off the folder.  But each and every file in it is still locked.  

But I notice the File Owner field is open and has a drop down menu that lists my user name.  If I choose that, I wonder what will happen.  Will that unlock all these files?  Will that allow RealPlayer to work? Will it restrict its use some way?  And so on.

---

