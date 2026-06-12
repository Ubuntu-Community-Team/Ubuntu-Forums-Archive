---
title: "searching for files"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by dravidan on 2008-03-12
I am trying to search for a directory in /us/local/include directory but nothing seemed to find it.  What is going on.  I can open the folder up using nautilus but just can't find it in any other way by searching for it.  Any idea?

---

### Post by ferdostar on 2008-03-12
> **dravidan said:**
> I am trying to search for a directory in /us/local/include directory but nothing seemed to find it.  What is going on.  I can open the folder up using nautilus but just can't find it in any other way by searching for it.  Any idea?

Maybe it's a hidden file/directory. Do Ctrl+H to see them

---

### Post by dravidan on 2008-03-12
I am able to see them under nautilus but can not see them using search for files or the find command from the terminal

---

### Post by LinuX-M@n1@k on 2008-03-12
the search feature in nautilus never worked for me... use this command in the terminal:
```
locate <folder.or.file>
```

---

### Post by castudil on 2008-03-12
In order to use locate properly, from time to time, you have to update the database of files.

```

sudo updatedb

```

it will ask you for your password, then work for a while. after it is done, the most recently files will be included and Locate will find them in a few seconds.

---

### Post by noynac on 2008-03-12
> **LinuX-M@n1@k said:**
> the search feature in nautilus never worked for me... use this command in the terminal:
```
locate <folder.or.file>
```

You can also try:

```
sudo find / -iname DirectoryName
```

Just insert the actual directory name. Some other thoughts:

* You may want to post the commands that you have been unsuccessful in using. It's difficult to help otherwise.

* I assume that "us" is a typo and should be usr.

* Be sure to check for correct capitalization.

---

### Post by ryanhaigh on 2008-03-16
The version of Nautilus provided in Ubuntu 7.10 (Gutsy) uses tracker to search for files. This means that only files which are indexed will be shown in the results. You can get around this by using the Find Files option in Places, installing [nautilus-search-tool]("apt://nautilus-search-tool") or if you are like me and don't use tracker you can follow my [howto on compiling nautilus without tracker]("http://ubuntuforums.org/showthread.php?p=4524368"), its easier than it sounds.

---

### Post by ramjet_1953 on 2008-03-16
Are you sure that the directory that you want isn't:

[COLOR="Blue"]/usr/local/include[/COLOR] ?

Regards,
Roger :cool:

---

