---
title: "permissions"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by hughlle on 2006-09-29
ok, noone seems to want to help with my other problems so here's another one.

when i goto propertes of a file or folder and click permissions i am not allowed to change any of the permisions, they are all greyed out and i'm told that i am not the owner so can't change anything.

i'm the only user and as such would ahev thought i'd be the "owner"

how do i become the "owner" so i can change permissions? ](*,)

---

### Post by Ben Sprinkle on 2006-09-29
> **hughlle said:**
> ok, noone seems to want to help with my other problems so here's another one.

when i goto propertes of a file or folder and click permissions i am not allowed to change any of the permisions, they are all greyed out and i'm told that i am not the owner so can't change anything.

i'm the only user and as such would ahev thought i'd be the "owner"

how do i become the "owner" so i can change permissions? ](*,)

su
chmod 777 file (Or)
chmod file 777
Try that mate.

---

### Post by hughlle on 2006-09-29
```
chmod file 777su: Authentication failure
```

? do i need to edit a file somewhere to enter myself as an SU?

---

### Post by Ben Sprinkle on 2006-09-29
> **hughlle said:**
> ```
chmod file 777su: Authentication failure
```

? do i need to edit a file somewhere to enter myself as an SU?

Erm.
You type su to let you have root rights.
Then type chmod 777.

---

### Post by hughlle on 2006-09-29
i know, but its not letting me have root rights, i type su, enter my password and then try that command and i get su authentication failure

---

### Post by Ben Sprinkle on 2006-09-29
> **hughlle said:**
> i know, but its not letting me have root rights, i type su, enter my password and then try that command and i get su authentication failure

That means you did not set the root password?
password root newpass
(I think)

---

### Post by jorn on 2006-09-29
Be careful changing permissions for files that belong to the system.
You will also be able to change permissions by opening terminal and type:
> gksudo nautilus
You become root. Make your changes and close.

---

### Post by crane on 2006-09-29
It really depends on the file or folder your wanting to change. If it is a system file it should probably stay as root.
 Sorry, Let me start over.
The permissions being greyed out because they are owned by the root user. It is a way of protecting the system.
 What exactly are you trying to change the permissions of. You should do this with caution, I have made the mistake of changing permissions on a file I shouldn't have and screwed up the system.
 Use the command
```
sudo chown yourname:yourname /path/to/file
```
this will change owner and group setting to you and yours.
```
sudo chmod -777 /path/to/file
```
this will change the permissions of a file so everyone has read/write/exec rights to the file.

 There are many switches for these commands. for further help type
```
man chown
```
or 
```
man chmad
```
in terminal

---

### Post by crane on 2006-09-29
> **Goat Spirit said:**
> That means you did not set the root password?
password root newpass
(I think)

Ubuntu does not have root user enabled.
Just use sudo command.

---

### Post by hughlle on 2006-09-29
well being root hasn't helped my situation. tried to change the permissions on a hard drive so that i could read it and got this  

"Couldn't change the permissions of "hda1" because it is on a read-only disk"

looks like i'm moving over to suse 10.1, never had issues with that

---

### Post by Ben Sprinkle on 2006-09-29
That is because you cannot write to ntfs without extensive work.

---

### Post by CadetD on 2006-09-29
> **Goat Spirit said:**
> That means you did not set the root password?
password root newpass
(I think)

minor correction:

passwd root yournewpassword
 ^^^

---

### Post by hughlle on 2006-09-29
as i said i was only trying to allow read access, not write, how come i can't do that.

one quick question though: is it actually possible to get simple file sharing working with ubuntu so that i dont need user accounts and passowrds. i just want to stream a file over the network withought having to copy the whole thing

---

### Post by tageiru on 2006-09-29
> **Goat Spirit said:**
> su
chmod 777 file (Or)
chmod file 777
Try that mate.

Giving out recommendations like that can seriously damage peoples installations.

---

### Post by CatKiller on 2006-09-29
> **hughlle said:**
> ok, noone seems to want to help with my other problems so here's another one.

That hardly seems like a fair comment. People seem to have been trying to help you in your other threads. It seems that you could do with some reading.

[File Permissions in Ubuntu]("http://psychocats.net/ubuntu/permissions")
[RootSudo wiki page]("https://help.ubuntu.com/community/RootSudo")
[How to mount Windows partitions on boot-up and allow all users to read only]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only")
[Mounting Windows Partitions in Ubuntu]("http://psychocats.net/ubuntu/mountwindows")

---

### Post by hughlle on 2006-09-29
appologies to hymntolife

am not in best of moods atm, been having a bit of a ruff week

---

### Post by Iowan on 2006-09-29
Looks like some interesting links in CatKiller's sig - some might help w/ current problem.

---

