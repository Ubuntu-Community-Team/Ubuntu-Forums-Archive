---
title: "Alert Pop-up"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by Kevin Funnell on 2006-09-16
G'Gay All,

I receive the following when startinb Ubuntu:
*[COLOR="Blue"]"User's HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User$Homedirectory must be owned by the user and not writable by other users"[/COLOR]*
I am the only user of this computer Windows Xp & Ubuntu, I do not know how I got myself in to getting this Alert message or how I can rectify this problem.  Any help or pointing me to correct this will be appreciated.

Thanks, Old Kevin](*,)

---

### Post by Kilz on 2006-09-16
> **Kevin Funnell said:**
> G'Gay All,

I receive the following when startinb Ubuntu:
*[COLOR="Blue"]"User's HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User$Homedirectory must be owned by the user and not writable by other users"[/COLOR]*
I am the only user of this computer Windows Xp & Ubuntu, I do not know how I got myself in to getting this Alert message or how I can rectify this problem.  Any help or pointing me to correct this will be appreciated.

Thanks, Old Kevin](*,)

I did that myself some time ago. Its nothing to worry about, open a terminal and type in ```
sudo chmod 644 .dmrc 
```
You might also have to do ```
sudo chown -R username:username /home/username

``` change all the username's to your login.

---

