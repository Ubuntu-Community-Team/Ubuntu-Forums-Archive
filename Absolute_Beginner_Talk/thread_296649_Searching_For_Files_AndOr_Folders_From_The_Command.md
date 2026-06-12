---
title: "Searching For Files And/Or Folders From The Command Line"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by Ireclan on 2006-11-09
How would one search the computer for a file or folder from the command line? The documentation I read in the system help says it should be "locate [File/Folder Name]", but doing this does nothing. Furthermore, a search of the man pages only yields up a command known as "slocate", but trying "slocate [File/Folder Name]" yields nothing either.

---

### Post by xlulux on 2006-11-09
try this to update your locate function.

user$updatedb
user$locate file

some files can only be found as root :-)

---

### Post by Ireclan on 2006-11-09
That's the thing, though. The file I created in order to test out my understanding of this command upon was created by me and placed in my home folder. Shouldn't it show up, since it was not root which created it?

---

### Post by po0f on 2006-11-09
Nomad O' North,

Have you ran the command xlulux posted to update slocate's index?  You might have to run it with root privileges:
```
$ touch ~/myfile
$ sudo updatedb
$ locate myfile
```

---

### Post by dannyboy79 on 2006-11-09
i don;t use locate, i use find. so if you wanted to find her within the root folder (which will search everywhere)

sudo find / -name her

and your golden baby!

---

### Post by po0f on 2006-11-09
dannyboy79,

Someone must like thrashing their hard disks needlessly, eh?  ;)

---

### Post by Ireclan on 2006-11-09
Thanks, guys/gals. I'll try those two things and report back.

---

### Post by bikeboy on 2006-11-09
To clarify a bit more, "locate" uses a database and finds results really quickly, but the database only gets updated occasionally (daily I think) so a new file won't be there straight away. But you can update it whenever you want with the command as mentioned above.```
sudo updatedb
``` 

Find doesn't use a database so it's slower, but it finds newly created files automatically. It works by typing find [path to start search] -name file. eg ```
find ~/ -name newfile
```

This will find the file called newfile in your home directory. You can also use things like "find ~/ -name new*" to find "newfile". Use sudo find if you need to search directories owned by root.

---

### Post by dannyboy79 on 2006-11-09
> **po0f said:**
> dannyboy79,

Someone must like thrashing their hard disks needlessly, eh?  ;)

if you are saying that this is bad, than could you explain instead of just telling me I am thrashing my hardrive?

does locate work with only knowing partial things, like say  I wanted to find anything that had the word log in it anywhere? i would do sudo find / -name *log*, would this also work with locate? if locates db has to updated once in awhile, maybe that would be a good job for cron?

---

### Post by bikeboy on 2006-11-09
Yep, *log* will work with locate. I think cron already handles the database update, that's how it gets automatically updated.

---

### Post by dannyboy79 on 2006-11-10
so that other's will know about the find command, this is what I was informed about find thrashing your HDD.

"`find` actively searches the files on your hard drive, meaning it will actually go through every single directory and file, reporting hits as it finds them. `slocate` builds an index daily of all the files on your hard drive, so when you `locate file`, it just looks in the index, instead of going through all the directories, thus saving needless thrashing of your hard drive."

---

