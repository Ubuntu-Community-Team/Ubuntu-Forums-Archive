---
title: "are permissions different between redhat and ubuntu?"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by iansane on 2008-03-24
Hi, Can anyone tell me if there are different permissions between Fedora and Ubuntu?

I'm having trouble writing to a virtual shared folder from Fedora VM on Ubuntu Server host.

I need to know if it is a permissions problem or something else. On the host I did "chmod  -R 0777 virtualShare" but in the guest I can only read and write to text files. I get errors if I try to create or rename a folder or copy any other type of file from guest into the folder.

If there are differences wheres a good source to read about them? Thanks

---

### Post by smartboyathome on 2008-03-24
Have you enabled sharing of shared folders with Virtualbox (I think it is in the settings page, but I don't know exactly because I don't have it installed on this machine). Other VMs I don't know.

---

### Post by scragar on 2008-03-24
drop the leading 0 from your perm's, it's not needed and could cause problems:
```
chmod -R 777 virtualShare
```
try running:
```
ls -l virtualShare
``` to see what it's perm's are, could be different for some reason.

---

### Post by joshrobinson on 2008-03-24
on the server computer can any user do anything? create or rename folders?

the fedora pc cant create or rename folders?
are you using samba?

---

### Post by iansane on 2008-03-24
Well I thought that 777 would mean anyone can do anything. Is that right? I also thought there were supposed to be 4 numbers because I've seen that before. Your suggestions seem to have fixed the problem.
```
ian@lotus-control:~$ ls -l virtualShare
total 12
drwxrwxrwx 2 ian ian 4096 2008-03-24 21:28 add
-rw------- 1 ian ian    0 2008-03-24 21:26 shrt
-rwxrwxrwx 1 ian ian   90 2008-03-24 21:20 test.txt
drwxr-xr-x 2 ian ian 4096 2008-03-24 21:26 untitled folder
ian@lotus-control:~$ sudo chmod -R 777 virtualShare
[sudo] password for ian: 
ian@lotus-control:~$ ls -l virtualShare
total 12
drwxrwxrwx 2 ian ian 4096 2008-03-24 21:28 add
-rwxrwxrwx 1 ian ian    0 2008-03-24 21:26 shrt
-rwxrwxrwx 1 ian ian   90 2008-03-24 21:20 test.txt
drwxrwxrwx 2 ian ian 4096 2008-03-24 21:26 untitled folder

```

Never mind the file names. Since I was testing, on some of them I just hit random keys and on two of them I had explicitly chmoded them.

Since I did -R will these permissions apply to any new files or folders I put in there?

---

### Post by iansane on 2008-03-24
thanks scragar.

---

