---
title: "trash bin"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by 1fastredsc on 2007-05-07
My trash bin keeps saying that there are 8 items in it no matter how many times i empty it. Any ideas?
I'm running ubuntu 7.04

---

### Post by fakie_flip on 2007-05-07
Do this to see what is really in your Trash bin.

ls -la ~/.Trash

Do this to empty your trash.

rm -irv ~/.Trash/* 

When I first began using Feisty, I had some bugs with my trash bin, but after doing an update, I got a bug fix and didn't have problems with it again. Try updating your system.

---

### Post by Abstraxis on 2007-05-07
Is there a way to setup the amount of space used by the trash bin?

---

### Post by fakie_flip on 2007-05-07
What do you mean? Did the commands help and did you do an update?

---

### Post by Abstraxis on 2007-05-07
Check the usernames, I'm not the one that started this topic. :)

---

### Post by 1fastredsc on 2007-05-07
rm: cannot lstat `/home/mike/.Trash/*': No such file or directory

That's the message i got when i used that command above to empty the trash bin.

total 8
drwx------  2 mike mike 4096 2007-05-07 10:12 .
drwxr-xr-x 29 mike mike 4096 2007-05-07 10:32 ..

And that is the message i got when i tried to see what's really in the trash bin.

---

### Post by fakie_flip on 2007-05-07
ls -la ~/.Trash

The one above shows hidden files.

du -sh ~/.Trash

Here is what I get.

chris@ubuntu:~$ rm -irv ~/.Trash/* 
rm: remove regular file `/home/chris/.Trash/00006.jpg.bz2'? 

So if it says directory not found on your computer, then you need to create it.

mkdir ~/.Trash

---

### Post by 1fastredsc on 2007-05-07
mike@mike-desktop:~$ ls -la ~/.Trash
total 8
drwx------  2 mike mike 4096 2007-05-07 10:12 .
drwxr-xr-x 29 mike mike 4096 2007-05-07 10:32 ..
mike@mike-desktop:~$ du -sh ~/.Trash
4.0K    /home/mike/.Trash
mike@mike-desktop:~$ ls -la ~/.Trash
total 8
drwx------  2 mike mike 4096 2007-05-07 10:12 .
drwxr-xr-x 29 mike mike 4096 2007-05-07 10:32 ..
mike@mike-desktop:~$ 
mike@mike-desktop:~$ mkdir ~/.Trash
mkdir: cannot create directory `/home/mike/.Trash': File exists
mike@mike-desktop:~$ 

That's all that i've been getting right there.

---

### Post by fakie_flip on 2007-05-07
delete your trash bin and then recreate it. it appears to be empty but it says "total 8". that is strange.

rmdir ~/.Trash
rm -rvf ~./Trash
mkdir ~/.Trash

---

### Post by cloud1 on 2007-05-09
> **fakie_flip said:**
> delete your trash bin and then recreate it. it appears to be empty but it says "total 8". that is strange.

rmdir ~/.Trash
rm -rvf ~./Trash
mkdir ~/.Trash

I was also having a different problem too. My problem was that I can't select the option 

"Empty Trash" when my trash can was not empty and I right-clicked on it. But deleting my .Trash

folder and recreating the .Trash folder solved the problem. Thanks fakie_flip.

---

### Post by fakie_flip on 2007-05-09
> **cloud1 said:**
> I was also having a different problem too. My problem was that I can't select the option 

"Empty Trash" when my trash can was not empty and I right-clicked on it. But deleting my .Trash

folder and recreating the .Trash folder solved the problem. Thanks fakie_flip.

You're welcome. I'm glad I could help you. Also keep your system up to date with the newest software, and you will have patches for bugs like these. You can use Synaptic, update-manager, or these commands to do it. Synaptic has a setting in preferences that will automatically download updates and tell you after it does. Then you can install them. You have to enable it if you want that.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by fakie_flip on 2007-05-09
Your problem may have been because of file permissions or a bug in Feisty. Keep your system up to date.

---

### Post by Fraoch on 2007-05-11
This is weird - I have two Ubuntu 7.04 setups.  On the older one, never a problem with the trash bin.  On the brand-new one I just had to go through this thread to correct the same problem the OP was having.

It was down to permissions - it wouldn't let me delete two archives that had root permissions on some of the folders compressed inside.  Seems simple enough, but I've done all sorts of things to my older box without this ever coming up once, and the install is very new on the new box and this issue cropped up right away?

Any ideas?  The second box is a 64-bit version, but that shouldn't affect this issue.  All software on both boxes is fully up to date.

---

### Post by fakie_flip on 2007-05-15
if you have something with root permissions in your trash bin, then you will need sudo to delete it.

sudo rm -iv ~/.Trash/*

---

