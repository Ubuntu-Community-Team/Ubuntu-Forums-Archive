---
title: "I chown'ed my /etc folder"
date: 2005-11-18
forum: Absolute Beginner Talk
---

### Post by norair on 2005-11-18
how do i undo the damage?
sudo: /etc/sudoers is owned by uid 1000, should be 0

i was trying to edit the fstab file, i really want to be able to mount my NTFS winxp harddrive

it shows up as /dev/sda1

---

### Post by gord on 2005-11-18
```
 sudo chown root /etc/sudoers 
```

should work, allthough its a little vauge as to what you want.

---

### Post by norair on 2005-11-18
[QUOTE=gord]```
 sudo chown root /etc/sudoers 
```

should work, allthough its a little vauge as to what you want.[/QUOTE]

norair@ubuntu:~$ sudo chown root /etc/sudoers
sudo: /etc/sudoers is owned by uid 1000, should be 0


didnt work, any other suggestions?

---

### Post by Chayak on 2005-11-18
Well since you chown'ed it you should be able to chown it back to root, try it without the sudo as sudo won't work anyway

```
chown root /etc/sudoers
```

Then again while you were at it I'd just chown the entire /etc back to root with the recursive option

```
chown -R root /etc
```

---

### Post by norair on 2005-11-18
[QUOTE=Chayak]Well since you chown'ed it you should be able to chown it back to root, try it without the sudo as sudo won't work anyway

```
chown root /etc/sudoers
```

Then again while you were at it I'd just chown the entire /etc back to root with the recursive option

```
chown -R root /etc
```[/QUOTE]

says im not permitted

chown: changing ownership of `/etc/update-notifier/hooks_seen': Operation not permitted

---

### Post by sjh on 2005-11-18
I don't know if this will help you but there is a -u option in sudo that will allow you to run the command as uid 1000.  I have never used it but it may be worth a try.

Good luck
SJH

---

### Post by doclivingston on 2005-11-18
Sudo will refuse to run if the permissions on /etc/sudoers is wrong, to prevent accidental security breaches. One way to fix it is to reboot into "recovery mode" (select from the grub menu) and use chown from there.

---

### Post by norair on 2005-11-18
[QUOTE=doclivingston]Sudo will refuse to run if the permissions on /etc/sudoers is wrong, to prevent accidental security breaches. One way to fix it is to reboot into "recovery mode" (select from the grub menu) and use chown from there.[/QUOTE]


awsome, you are the man... it got me into root and the rest explains itself

---

