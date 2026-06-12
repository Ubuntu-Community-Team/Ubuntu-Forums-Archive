---
title: "problems with using tar to make backup"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by hikitsu4 on 2006-07-03
Can somebody help me with this syntax with tar.

first i do sudo su
then i do cd /tmp
then i do tar cvpzf backup2.tgz /home/mynickname --exclude=/home/mynickname/folder1

the problem is that even if i use the exclude command it still packs that folder. So i need some help with why it doesnt exclude that folder. 
And also it seems it doesnt pack down all files i dont know why. (most of the files and folders it packs down just not all it seems)

---

### Post by Arndt on 2006-07-03
[QUOTE=hikitsu4]Can somebody help me with this syntax with tar.

first i do sudo su
then i do cd /tmp
then i do tar cvpzf backup2.tgz /home/mynickname --exclude=/home/mynickname/folder1

the problem is that even if i use the exclude command it still packs that folder. So i need some help with why it doesnt exclude that folder. 
And also it seems it doesnt pack down all files i dont know why. (most of the files and folders it packs down just not all it seems)[/QUOTE]

I think what you want is:
```
tar cvpz --exclude=/home/mynickname/folder1 -f backup2.tgz /home/mynickname

```

--exclude is an option and must be specified before the files to pack. Also, 'f' must still be followed directly by the file argument, and apparently a hyphen is needed if the single-letter options are not first. Did you get an error from 'tar' "Can't stat --exclude" or something like that?

Why it doesn't pack all files, I don't know.

---

### Post by thk on 2006-07-03
Tar typically strips the leading / from file names so you can restore easily to a new location. Since /home... is never listed, it can't be matched. Try omitting the leading / from the exclude statement. You can modify this behavior with switches.

---

### Post by hikitsu4 on 2006-07-03
[quote=Arndt]I think what you want is:
```
tar cvpz --exclude=/home/mynickname/folder1 -f backup2.tgz /home/mynickname

``` 
--exclude is an option and must be specified before the files to pack. Also, 'f' must still be followed directly by the file argument, and apparently a hyphen is needed if the single-letter options are not first. Did you get an error from 'tar' "Can't stat --exclude" or something like that?

Why it doesn't pack all files, I don't know.[/quote]
ok it seem to have worked when i open the tgz file with fileroller i see first home then in that mynickname.
How do i do about when i want to revert/overwrite to the backup (with tar in the command prompt).

---

