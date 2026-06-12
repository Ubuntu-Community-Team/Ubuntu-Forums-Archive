---
title: "Folder stuck in my Desktop."
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by RobyX on 2006-04-26
I got this RealPlayer folder stuck on my Desktop i've tried deleting it with
sudo nautilus.

But in the file browser it come's up empty. I'll let the screenshots speak for itself. ;) 

[http://img134.imageshack.us/img134/87/screenshot19fv.png](http://img134.imageshack.us/img134/87/screenshot19fv.png)
[http://img267.imageshack.us/img267/1975/screenshot8in.png](http://img267.imageshack.us/img267/1975/screenshot8in.png)

---

### Post by hollywoodb on 2006-04-26
try 'sudo ls -al /home/roby/Desktop'

if your RealPlayer directory shows up there, 

'sudo rm -r /home/roby/Desktop/RealPlayer'

chances are the directory was created without your user (roby) having ownership of it.  in order to keep the directory but regain ownership:

'sudo chown -R roby:roby /home/roby/Desktop'

---

### Post by RobyX on 2006-04-26
[QUOTE=hollywoodb]try 'sudo ls -al /home/roby/Desktop'

if your RealPlayer directory shows up there, 

'sudo rm -r /home/roby/Desktop/RealPlayer'

chances are the directory was created without your user (roby) having ownership of it.  in order to keep the directory but regain ownership:

'sudo chown -R roby:roby /home/roby/Desktop'[/QUOTE]

It worked , thanks man.

---

