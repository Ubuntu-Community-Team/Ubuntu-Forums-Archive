---
title: "please help me"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by ubunlilluz on 2006-07-16
hi,
i'm desperate, tryng to cancel some files in the trash i defined to 777 the permission of all hd's file. Now all things that required the sudo don't work and i guess the system is in danger. If i trie to do "chmod 0440 sudoers" (operation advised by the system) it says that the operation isn't allowed.
Please help

---

### Post by pimeja on 2006-07-16
You can't switch to root. Do I understand correct you?

I think command "su" help you.

[FONT="Lucida Console"][~] % whereis su
su: /bin/su /usr/share/man/man1/su.1.gz

[~] % dpkg -S /bin/su
login: /bin/su[/FONT]

---

### Post by adam.tropics on 2006-07-16
```
sudo su

```
then

```
chmod 0440 sudoers
```

---

### Post by ubunlilluz on 2006-07-16
i solved this first part turning to recovery mode: now sudo works and all sw that require it. 
Now i need to solve two problems that appears: at boot it says that home/.dmrc will be ignored (or something like that) because it require permission 644 and that the dyrectory home must be of the proprity of the user and not of anyone (now it's 777). I modified first .dmrc permission and the message appeared again, then i tried to change home permission and its subfolder to 740 but i had to come back to recovery mode and turning home to 777 because i couldn' use anything on acount of permission.
what is the right way to set home permission?

---

### Post by ubunlilluz on 2006-07-16
other question : is my system safe now with many files (not all,i checked)  in the filesystem folder with permission 777

---

### Post by bluecherry on 2006-07-16
Nope it's not safe.

1. If any program running on your computer has an (still to be discovered) security issue and allows for a "bad person" to gain control over your pc he will have access to all your files. 
-> How big is the chance that anybody wants to take over your pc? You're decision.

2. You yourself are perhaps the biggest threat: you might delete important files by accident, mistype some file manipulating command or whatever... ;)

---

### Post by [S|G] on 2006-07-16
You definitely have a serious security issue, not to mention that the system will refuse to run several programs and perform several actions due to wrong permissions on sensistive files.

As bluecherry noted, you might be the biggest danger to the system now, since you have root-like access to everything. I can't think of an easy way to fix this without a clean reinstall. If you have your home directory in a separate partition, just go for it. 

An alternative way would be to first cut access from every user to vital files:
```

sudo chmod 744 / -R

```

That will make everything read-write-execute for the owner and read only for anyone else. There are some system files that are not readable by anyone but the owner, others are read-writable by the group and no-one else (such as /dev/dsp* devices... you would probably break your sound when you do that). 

In other words, fixing it by hand would require an enormous ammount of time and effort. That is why I suggest a clean reinstall if possible.

And never, ever, abuse root powers. Try not to mess with the system itself whenever possible. Your home folder is pretty much everything you need to mess with regularly.

---

### Post by ubunlilluz on 2006-07-17
i've decided to reinstall all. I got a separate partition for home,
do i need to do a backup of it?
thanks

---

### Post by [S|G] on 2006-07-17
If your /home is in a separate partition, you won't lose any of its data when you reinstall. Just make sure not to tell the installer to format it, and instead use it as the new /home.

---

