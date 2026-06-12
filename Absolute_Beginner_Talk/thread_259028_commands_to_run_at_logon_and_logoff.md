---
title: "commands to run at logon and logoff"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by neill on 2006-09-16
hi

i have some commands i want to run at user login and logout

they relate to mounting and umounting network shares

how do i write the scripts exactly and where do i put them and what permissions do they need and who 'owns' them (user or root) ??

thanks

neill

fyi
at logon: mount -t smbfs //server/share  /home/user/files
at logoff : umount /home/user/files

i don't want to have to enter the sudo password every time - it should just happen !!! :rolleyes:

---

### Post by Kilz on 2006-09-16
> **neill said:**
> hi

i have some commands i want to run at user login and logout

they relate to mounting and umounting network shares

how do i write the scripts exactly and where do i put them and what permissions do they need and who 'owns' them (user or root) ??

thanks

neill

fyi
at logon: mount -t smbfs //server/share  /home/user/files
at logoff : umount /home/user/files

i don't want to have to enter the sudo password every time - it should just happen !!! :rolleyes:


You could add them to fstab and have them automount if you want. You will have to make sure the smbfs package is installed, it isnt part of samba. Then open fstab
```
gksudo gedit /etc/fstab
```
Then add the line, making sure the folders /home/user/files exist.

```
//server/share    /home/user/files      smbfs    username=Guest,password=,fmask=777 0 0
```

---

### Post by neill on 2006-09-17
hi

the code works insofar as i have tested it at the CLI

the next step now is to automate the process

so when user X logs on a script is run that mounts a given share from the server and when he logs off that share is umounted again

i can do the commands, i just don't know how to convert them to scripts and where to put the scripits so they run appropriately

thanks

neill

---

### Post by neill on 2006-09-17
oh yeah i forgot

if i put the commands in fstab - does that mean the shares are loaded at boot, not logon ? :confused:

---

### Post by andb on 2006-09-17
Using Gnome,
System > Preferences > Sessions > third tab, Startup Programs

You can call a script from here at login. It will then be user specific.

I think that there is also something that could be used globally in the /etc/X11 directory if I remember.

Logout, hmmm, never needed it, so Im not sure.

---

### Post by neill on 2006-09-17
actually if i mount using fstab then it'll be unmounted at shutdown which for my purposes is fine

thanks y'all O:)

---

