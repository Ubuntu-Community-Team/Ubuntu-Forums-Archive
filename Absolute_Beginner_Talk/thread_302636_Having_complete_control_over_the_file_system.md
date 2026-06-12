---
title: "Having complete control over the file system"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by pastorjay on 2006-11-18
Can someone help me set my install up to allow me to have the ability to view all the files on my computer and edit them as I need to.  For instance, I need to delete the file "/etc/apt/preferences"

but i cannot get to it unless I go to console and type "sudo gedit /etc/apt/preferences"

So, am i able to do this?  

Thanks!

---

### Post by jordanmthomas on 2006-11-18
To delete a root-owned file, do this:
```
sudo rm */path/to/file*
```

Of course, be careful and be certain you want to do this.  It might be wiser to rename the file
```
sudo mv */path/to/file* */path/to/newfile*
```

---

### Post by ewl1217 on 2006-11-18
You could give yourself full root privileges, but that is unsafe and I'm not sure how exactly to do it. If you want to manage files with full root permissions, use the following command:
```
gksudo nautilus
```
Just take extreme caution in what you do... one wrong click and you could do a lot of damage.

---

### Post by Larry Roll on 2006-11-19
I tried to install a music player application, and I wasn't allowed to drag the plug-in file into the directory. If I give myself full root privileges by using this command, does this fix the problem?  

I am an absolute newbie.  I need the answer with the training wheels ON!  Thanks!

---

### Post by jordanmthomas on 2006-11-19
yes, gksudo nautilus will allow you to drag and drop things where you want and to change permissions accordingly.

---

### Post by msak007 on 2006-11-19
> **Larry Roll said:**
> I tried to install a music player application, and I wasn't allowed to drag the plug-in file into the directory. If I give myself full root privileges by using this command, does this fix the problem?  

I am an absolute newbie.  I need the answer with the training wheels ON!  Thanks!
Yes, opening Nautilus as root or using "sudo" before a command using the terminal *will* give you complete control over the system or command - but as others warned just be careful with it (especially a root Nautilus). You are used to the way Windows does things, which is basically allowing anybody to do anything they want. This is the reason Windows is so plagued with viruses and malware...basically any user has "root" privileges and can change system files, and any app a user runs can run rampant on the system and change or delete critical system files. Only use root privileges temporarily to do the action you need, then exit that mode and go back to being a regular user. You'll soon get used to it and realize it's a much better and secure way of doing things.

---

### Post by pastorjay on 2006-11-19
Thanks!  I was able to do what was needed!

---

