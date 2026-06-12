---
title: "scripting"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by tieflingrogue on 2008-01-27
I'm trying to modify the output of the ls -l command so that the file owner field is replaced with the file owner's user id number.   I've been trying something like   ```
ls -l | awk '{.............
```  combined with ```
grep ....... /etc/passwd
``` to find the user id, but no luck yet.

---

### Post by emarkd on 2008-01-27
I'm not much of an awk scripter, so I can't help you with the direction you're going.  If I were trying to do this, I'd probably go with Python and try to do something like this:

1.  os.popen the ls -l command and store the output in an array
2.  read through the /etc/passwd file and use regular expressions or something to extract a map for username: userid
3.  loop through your original array and use string substitution to swap in the mapped values while you print it back out to the terminal.

Yes, I realize this is very vague and just meant to give you an overall idea.  I leave it up to you to flesh this out more fully.  Have fun :)

---

### Post by bodhi.zazen on 2008-01-27
how about 

ls -n

---

### Post by bodhi.zazen on 2008-01-28
Save this file in ~/bin, call it what you wish (lsn ?)

> #!/bin/bash

# lsn by bodhi.zazen
# use lsn <dir>
# <dir> = directories to list
# ex : lsn / /bin

IFS=$'\n'

for i in `ls -l "$@"` ;do echo "$i" | while read line; do
u=`echo "$line" | awk '{print $3}'`
n="`grep -m 1 "$u" /etc/passwd | cut -d : -f 3`"
if [ -n "$u" ];
then
     echo "$line" | sed "s_"${u}"_"${n}"_"
else
     echo "$line"
fi
done
done 2>/dev/null

Make it executable ( ? by all)

```
chmod a+x ~/bin/lsn
```

* add ~/bin to your path

now you can :

lsn <dir> :

> bodhi@GutsyVZ:~$[color=blue]]lsn /[/color]
total 84
drwxr-xr-x   2 [color=blue]0[/color] root  4096 2007-11-04 23:43 bin
drwxr-xr-x   3 [color=blue]0[/color] root  4096 2007-11-05 02:22 boot
lrwxrwxrwx   1 [color=blue]0[/color] root    11 2007-11-04 23:18 cdrom -> media/cdrom
drwxr-xr-x  13 [color=blue]0[/color] root  5300 2008-01-27 14:31 dev
drwxr-xr-x 105 [color=blue]0[/color] root  4096 2008-01-27 14:33 etc
drwxr-xr-x   3 [color=blue]0[/color] root  4096 2007-11-04 23:32 home

<clip> you get the idea



---

