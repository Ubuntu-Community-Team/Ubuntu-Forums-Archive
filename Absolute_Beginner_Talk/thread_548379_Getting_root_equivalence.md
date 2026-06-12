---
title: "Getting root equivalence?"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by Shlomir on 2007-09-11
Ubutnu gets you to set up a user, however that user isn't root. 

How do you give your standard user root equivalence. I can logon as root or 'su' from command line, but I can't give myself access to a folder, or to give all users full access to particular folders..

In this case the folder is /dev/raw1394   ...I can't get my firewire interface to work properly becuase it claims my logon doesn't have access to it, so the Million dollar question is...how do I do it?

Cheers and thanks.

---

### Post by jw5801 on 2007-09-11
Anything in /dev/ isn't actually a folder per se, it's a reference to hardware. So your hard drives are in there, your mouse, any joysticks etc. But anything with a filesystem on it needs to be "mounted" to a different location before you can do anything to it. What are you trying to do with your firewire interface and what happens when you do it?

As for changing the access to particular folders, look into chmod ```
man chmod
```the man page can be heavy reading, but it makes sense in the end. chmod is used to change the permissions on a directory or file, to give a user, a group of users or all users, either read, write or execute permissions (or all three).

---

### Post by asmoore82 on 2007-09-11
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Shlomir on 2007-09-11
I'm trying to do this, but new folder I created as root 'root' won't let me change the access right when using my current user..

Likewise, when I try sudo -s, I still can;t do it..Whe I used the graphic file browser I can't create a new folder in that share as it say that 'root' is the owner!


This is confusing and frustrating, any clear help would be appreciated!

---

### Post by jw5801 on 2007-09-12
sudo -s will only change the use for that shell. So if you change to root in the terminal then it won't make any difference to nautilus (the file browser). If you want to be the owner of the folder then go: ```
sudo chown *your-username /folder-you-want-to-change*
```

---

