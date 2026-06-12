---
title: "[SOLVED] Admin. Permission"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by ameanjoe on 2008-03-23
I read the thread by redarrow01 in General Help and thought it might help my problem, but....
I mistakenly created a folder which was placed on my desktop while I was trying to install Google Earth with Synaptic. That didn't work, but when I closed all of the windows, there was this empty folder on the desktop and when I tried to delete/move to trash/... I get this message:
"Cannot move "/home/joe/Desktop/new folder" to trash because you do not have permission to change it or its parent folder".
I am the only user of this computer...The Admin....Tried reinserting my password every way I could think of...Read everything I could find in all of the various documentation, but nothing seems to work. BTW, I am running Ubuntu 7.10 on a fairly new Dell...Just made the change over from Win XP, and have a lot to learn...HELP

---

### Post by kbless7 on 2008-03-23
Press <alt>f2. then enter
```
gksudo nautilus
```

this will open the root folder with root permissions. take care of whatever you need then

---

### Post by freebeer on 2008-03-23
The simple way:

Launch a terminal window and type (or copy & paste) this:

```

gksudo nautilus

```

you will be prompted to type in your password.  Type it in and hit enter.  (You won't see your characters being typed -- that's normal).

This will launch a copy of Nautilus.  Navigate to your Desktop.  You should see the folder and be able to delete it now.

What did this command do?  It launched Nautilus with "super user" privileges.  Under normal circumstances, although you are the "admin", it is unsafe to run with "admin" powers all the time.  So under normal conditions you operate at a regular user with privileges limited to routine things.  When you want or need "admin" privileges, you grant them to yourself with the "sudo" command.

---

### Post by Oldsoldier2003 on 2008-03-23
don't forget to empty root's trash if you use nautilus to delete files.

---

### Post by ameanjoe on 2008-03-23
Thank You to all that replied....It was so simple that I did not think of it...Trying to learn....
Mahalo nui loa, joe

---

