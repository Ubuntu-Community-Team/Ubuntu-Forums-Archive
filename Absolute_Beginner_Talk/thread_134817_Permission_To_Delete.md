---
title: "Permission To Delete"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by jasrog on 2006-02-22
I have photos in my home folder I want to delete but it says I don't have permission to delete, I am adminstrator how can I delete these?

---

### Post by Brunellus on 2006-02-22
1) don't log in as root. Use sudo.

2) the files are probably owned by some other user.  If you want to get rid of them, just 

sudo rm 

them.

if it's a directory, its

sudo rm -rf

---

### Post by jasrog on 2006-02-22
Actually It Is my folder Because I am the only user....So how exactly do I do this??

---

### Post by taurus on 2006-02-22
To remove the folder and everything else in it, assuming you are the owner, 

rm -rf <name of folder>

---

### Post by steve.horsley on 2006-02-22
Someone else must have put them there. If you're the only user, then it must have been you while you were working as root (you can issue a command as root py preceding it with **su**). In this case, just delete them as root like this:
**sudo rm filename**
or have root give them to you:
**sudo chown jasrog:jasrog filename**

If there's a lot to do, you can use **gksudo nautilus** to launch a file manager window with root privilege, but **be careful** because you have the right to delete the whole filesystem.

P.S. 
From a command prompt, ls -l will show you who owns the file, or right-click in Nautilus and see Properties/Permissions

---

