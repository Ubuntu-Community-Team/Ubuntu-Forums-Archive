---
title: "chmod, sudo, and a folder in /mnt question"
date: 2005-05-16
forum: Absolute Beginner Talk
---

### Post by NoTiG on 2005-05-16
Hey i have a question. i created a folder in /mnt called storage

sudo mkdir /mnt/storage

and i cannot access it with my normal user... or with the sudo command.

sudo cd /mnt/storage  : sudo: cd: unknown command...

so i was trying to change permissions on the /mnt/storage file to allow all users to read it

sudo chmod a=r /mnt/storage

and the command goes through but i still cannot read storage

cd /mnt/storage Permission denied.

SO i was wondering whats going on ? am i going to have to use the root terminal every time i want to read files of another mounted partition??

---

### Post by Stormy Eyes on 2005-05-16
Try making **/media/storage** and mounting the volume at **/media/storage** instead of **/mnt/storage**.

---

### Post by NoTiG on 2005-05-16
[QUOTE=Stormy Eyes]Try making **/media/storage** and mounting the volume at **/media/storage** instead of **/mnt/storage**.[/QUOTE]

I tried... Nope it didn't work. in case anyone is wondering the permissions on the folder are:

ls -l

dr--r--r--  22 root       root       4096 2005-05-10 20:18

---

### Post by Stormy Eyes on 2005-05-16
[QUOTE=NoTiG]I tried... Nope it didn't work. in case anyone is wondering the permissions on the folder are:

ls -l

dr--r--r--  22 root       root       4096 2005-05-10 20:18[/QUOTE]

Try the following commands, then.  Substitute your user name for $USERNAME.
[indent][i]sudo chown $USERNAME:users /mnt/storage
sudo chmod a+rw /mnt/storage[/i][/indent]

Since it's still owned by root, you can't access it.

---

### Post by NoTiG on 2005-05-16
notig@ubuntu:/mnt$ sudo chmod a+rw /mnt/storage
notig@ubuntu:/mnt$ ls -l
total 4
drw-rw-rw-  22 notig users 4096 2005-05-10 20:18 storage
notig@ubuntu:/mnt$ cd
notig@ubuntu:~$ cd /mnt/storage
bash: cd: /mnt/storage: Permission denied

hmmmmmmmm . weird. on my other partition... with 32 bit ubuntu... I don't have this problem.

---

