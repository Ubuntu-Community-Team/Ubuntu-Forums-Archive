---
title: "Change file permissions"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by puppy on 2006-10-09
Hi folks, sometimes when I copy files to my home folder from a DVD-RW or indeed from my mounted NTFS partitions, they come over as locked (i.e. owned by Root)

Can anyone advise how to 
a) change ownership of these files &
b) how to stop ubuntu from copying files and locking them as it does so...

Any advice appreciated

---

### Post by Darrious on 2006-10-09
I usually do chmod 777 or chmod 666

Forget which one is which.

---

### Post by timnoc1456 on 2006-10-09
desktop$ sudo chmod -Rv 777 <filename> for full file permission.

---

### Post by Arby on 2006-10-09
In answer to part a); you can change the ownership of files with the chown command. At the commandline type: 

```
sudo chown user file 
```

where user is the user you want to change ownership to not the current owner and file is obviously the file you want to change the ownership on. You can get more options for the chown command by typing chown --help and as always the man page is at man chown. A useful relation of chown is chmod which allows you to change read/write/execute permissions without changing ownership of the file.

With respect to b) can't really help. It might have more to do with the permissions the files had when they were burnt to the DVD which would depend on which user was running the cd burner but that's just a guess.

Hope that helped

---

### Post by taurus on 2006-10-09
When you copy a file from a CD to your harddrive, it will reserve the same permission at on your CD.  So, you need to change it by hand then...

---

### Post by puppy on 2006-10-10
The "chown" command worked perfectly - thanks. I'd copied some documents from a DVD-R over into my home folder and they were all locked as being owned by root. After navigating to /home/pete/documents and then issuing the command:

sudo chown pete *.* 

all my documents now belong to me again :D 

Naughty Root [-X

---

