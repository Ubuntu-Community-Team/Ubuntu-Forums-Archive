---
title: "a few questions from a noobie"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by bigb0i on 2007-12-18
what is a common gnu program is used to archive files and folders?
what command would combine the three files a.txt,b.txt and c-index.txt?
what should all script files start with?
how do you restict the execution of a file to a particular grou?

thanks,

---

### Post by ctyc on 2007-12-18
1) tar
2) cat
3) the "she bang line"
4) chmod

---

### Post by LaRoza on 2007-12-18
> **ctyc said:**
> 
3) the "she bang line"


```

#! /usr/bin/sh

```

---

### Post by bigb0i on 2007-12-18
what is the "she bang line" o_o i'm a noobie >.<

---

### Post by nowshining on 2007-12-18
what is a common gnu program is used to archive files and folders?

fileroller and u can find xarchive in the synaptic package manager and fileroller is incl. with ubuntu

what command would combine the three files a.txt,b.txt and c-index.txt?

IDK that one :( sorry

what should all script files start with?

nothing u don't even have to extension it, just create a new document via right-clicking and open it up with gedit, input the script inof save and right click on the script -properties-- --tab -- permissions-- and make sure u set the permissions for the ability to execute the script urself. IF talking about inside

for bash scripts:
#!/bin/bash

for python scripts:

#!/usr/bin/perl -w

how do you restict the execution of a file to a particular grou?

right click the file --properties-- --tab -- permissions-- and in the drop down boxes choose the owner, and under group choose the group and under others choose none or the dotted line and hit apply permissions.

---

### Post by Paul133 on 2007-12-18
To elaborate, tar is a program/utility that will make files into an archive (usually .tar). Check out 'man tar' in a terminal to see how to tar things, untar them, and compress them with different compression algorithms. Cat will concatenate files so that 'cat file1 file2 file3' will make one file that adds them all together. 'Cat file1' will simply send the contents of file1 to stdout (the display). Shell programs should start with '#!/bin/sh' or '#!/bin/bash' depending on the shell used (sh or bash). Chmod allows you to change the permissions for a file. Do 'man chmod' in a termina to learn more about that. Chgroup allows you to change the group ownership of a file, as does chown. Again, 'man chgroup' or 'man chown' will give you more information on that. Hope this helped!

---

### Post by LaRoza on 2007-12-18
> **bigb0i said:**
> what is the "she bang line" o_o i'm a noobie >.<

I posted it above, but I'll explain it.

An executable text file that begins with has the "shebang" symbol, which is "#!" is used to point to the interpreter of the file.

So, ```
#! /usr/bin/python
``` is used in Python programs. There are other things one could use in case Python is not installed there.

For a shell script, you use what I posted or bash.

---

### Post by bigb0i on 2007-12-18
thanks guys,
i got two more questions that i would like to ask

how do i...

write a cron entry to display "happy new year" at midnight of the jan 1 each year in the motd

and

how do i write a cron entry to display "happy independence day" at noon on july 4th each year?

happy holidays to you guys!thanks again!

---

### Post by thelatinist on 2007-12-18
If you are looking for a GUI archiver, I suggest Xarchiver.  It will handle pretty much any format.

If you are looking for a command line tool, why not use tar?  To archive and gzip files:

```
tar cvzpf archive_name.tgz a.txt b.txt c-index.txt 
```

To unzip them:

```
tar xvzpf archive_name.tgz
```

You might want to put these files in a directory first if you are going to share them.  It is considered polite to prevent such files being scattered through their directories.

If you mean bash scripts, then:

```
#!/bin/bash
```

To change the permissions for a file you can right click on it in Nautilus and choose properties, or if you prefer the terminal:

```
sudo chown username:groupname *filename*
sudo chmod o-x *filename*
```

Of course, repalce username, groupname, and filename with the correct information for your situation.

---

### Post by carverj on 2007-12-19
> Chgroup allows you to change the group ownership of a file, as does chown. Again, 'man chgroup' or 'man chown' will give you more information on that. Hope this helped!

Paul 133 is correct, only take a look at 'man chgrp'

> how do i...

write a cron entry to display "happy new year" at midnight of the jan 1 each year in the motd


Hi,
     Perhaps a new thread here will help you find an answer. Check /etc/crontab file and each of the 5 entries (minute, hour, day of week, etc.) would be 30 and 12 for 12:30 (midday), day of week is 0 or seven for Sunday I believe. So Monday would be 1. Just trial and error I believe

Merry Chrissy all!!

---

