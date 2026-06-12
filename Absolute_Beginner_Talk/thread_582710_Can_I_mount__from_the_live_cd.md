---
title: "Can I mount / from the live cd"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-10-20
I messed up pretty good. Now I need to get some pics off my hard drive. It was a default guided install using the whole hard drive so the partitions are default. What I did was try to change the permitions of my entire file system by doing 
"sudo chmod 755 -R /" it was just an experiment. I forgot my girlfriend put those pics on there. Anyways now I can't log on because I don't have permition to use the file that accepts my login password. So either I need a command that will reverse what I did, or a way to get those pics with live cd. Can someone help me out please? Thanks!

---

### Post by argie on 2007-10-20
Ouch, that wasn't a great idea. Okay, how many drives (not partitions) do you have? If it's only one, then do this from the LiveCD:
List all partitions on the first drive:
```
sfdisk -l /dev/sda
```
See if you can find your / partition there (something like /dev/sda1) . Then make a directory in your home folder.
```
mkdir harddrive
```
Then mount that part:
```
sudo mount /dev/sda1 ./harddrive -t ext3
```
Now just take your files from the harddrive folder. I'll try this myself once I can find my Feisty LiveCD and see. Doesn't the LiveCD simply mount all drives under /media anyway?

---

### Post by swoll1980 on 2007-10-22
Thanks

---

