---
title: "linux command for showing text file"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by tadashi on 2006-05-27
I am looking for a linux command to show my text file.  The kicker is that it is my ftp.log file and I want it to show anything added to the file until I ctrl+C out of it.  I tried to do cat for that will just show the file and end.  Any ideas?

---

### Post by aysiu on 2006-05-27
You could try nano: ```
nano ftp.log
```

---

### Post by tadashi on 2006-05-27
Nope.  I do not have the nano command it seems.

---

### Post by Shay Stephens on 2006-05-27
try vi instead of nano

```
vi ftp.log
```

It is more fiddley to work with than nano but should come installed.  If you don't like vi, install nano.

---

### Post by IYY on 2006-05-27
I'm sure there's a program to do what you want, but for now you could do something like

while true; do clear; cat log.txt; sleep 1 ; done

---

### Post by Rinzwind on 2006-05-27
Wasn't it
**tail**
to show the last few lines of a file?

> TAIL(1)                          User Commands                         TAIL(1)

NAME
       tail - output the last part of files

SYNOPSIS
       tail [OPTION]... [FILE]...

DESCRIPTION
       Print  the  last  10  lines of each FILE to standard output.  With more
       than one FILE, precede each with a header giving the file  name.   With
       no FILE, or when FILE is -, read standard input.

       Mandatory  arguments  to  long  options are mandatory for short options
       too.

       --retry
              keep trying to open a file even if it is inaccessible when  tail
              starts  or if it becomes inaccessible later; useful when follow&#8208;
              ing by name, i.e., with --follow=name
<..>
-f, --follow[={name|descriptor}]
              output appended data as the file grows; -f, --follow, and --fol&#8208;
              low=descriptor are equivalent

<..>
       -s, --sleep-interval=S
              with -f, sleep for approximately S seconds (default 1.0) between
              iterations.


Semi-tested-example:

tail --retry --follow=name --sleep-interval=2 /var/log/messages

should recheck /var/log/messages every 2 seconds for changes.

---

### Post by hobbit1983 on 2006-05-27
If you haven't got the nano application (but would like it)

in a terminal window type 

sudo apt-get install nano

and nano will be installed for you

---

### Post by mlind on 2006-05-27
if you just want to look a file, good commands are
```

less *file*
more *file*
cat *file*

```

or even cat *file* | less

---

### Post by hw-tph on 2006-05-27
[QUOTE=mlind]or even cat *file* | less[/QUOTE]

There is a prize that is awarded once a year for "useless use of the cat command". This is a strong candidate as it does the same thing as **less file**. :P


Håkan

---

### Post by mlind on 2006-05-27
[QUOTE=hw-tph]There is a prize that is awarded once a year for "useless use of the cat command". This is a strong candidate as it does the same thing as **less file**. :P


Håkan[/QUOTE]

lol :mrgreen: 
how about less file | cat | more

---

### Post by ifokkema on 2006-05-27
[QUOTE=tadashi]The kicker is that it is my ftp.log file and I want it to show anything added to the file until I ctrl+C out of it.[/QUOTE]

Use tail, with the -f flag. This will output the last 10 lines of the file and show you new lines as they are appended to the file. Use the -n flag to show more lines at startup.
So to show the last 20 lines and keep showing new lines as they are appended:
```
tail -n 20 -f /path/to/logfile
```

Ivo

---

### Post by sam hassell on 2006-05-27
tail -f is one of my favorite commands :) great for catching errors as they occur.

---

### Post by tadashi on 2006-05-27
Sweet thanks that was it.  tail -f

I used to use it with my simulations logs but could not remember what it was.

---

