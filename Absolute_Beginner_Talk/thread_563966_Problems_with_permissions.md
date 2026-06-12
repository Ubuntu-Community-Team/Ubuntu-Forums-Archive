---
title: "Problems with permissions"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by jcorden on 2007-09-30
Simple question from a real dunce.

I have 2 users set up on my system (myself and my wife). I would like to share the directory that we store digital photo's in so we can both read and write to this directory. I am the administrator and set up as 'james', my wife is set up as 'caroline'.

The path to the folder with the images in is /home/james/Pictures (pretty original folder names!)
I am the owner of this directory.

I thought I could share this by adding users 'james' and 'caroline' to the 'users' group and then changing the group of the directory to 'users'. I did this and these are the current permissions for this directory.

drwxrwxr-x 24 james users  4096 2007-09-30 20:17 Pictures

However when I log in as 'Caroline' this directory does not appear to be accessible.

Could someone please advise how best to set up directories that multiple users can share?

Thanks

---

### Post by Billy_McBong on 2007-09-30
[COLOR="Blue"]i think
```
sudo chmod 777 [path to folder]
```
should make it accessible to both of you[/COLOR]

---

