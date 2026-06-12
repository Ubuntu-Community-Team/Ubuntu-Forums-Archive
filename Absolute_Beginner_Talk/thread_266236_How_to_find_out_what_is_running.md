---
title: "How to find out what is running"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by itisgood on 2006-09-27
hi everyone,

i am tring to find out something like the "system manager" in windows, that could let me know what is actually running on my Ubuntu, what should I type.

and in the following command

postgres@jyao-laptop:/usr/bin$ pg_ctlcluster start
Usage: /usr/bin/pg_ctlcluster <version> <cluster> <action>
postgres@jyao-laptop:/usr/bin$

what does the second line mean? 
"Usage: /usr/bin/pg_ctlcluster <version> <cluster> <action>"

does it mean i have typed in something wrong or that command has worked?
thx

---

### Post by bodhi.zazen on 2006-09-27
In a terminal type:

```
top
```

OR ```
ps -ax
```

---

### Post by Indras on 2006-09-27
The program you're looking for is System Monitor.  System->Administration->System Monitor.  From command line, you can type 'ps -x' to get a list of all processes running on your system in similar fashion.

The line:
```
Usage: /usr/bin/pg_ctlcluster <version> <cluster> <action>
```
Means that in order to properly use the command, you must first fill in the blanks <version>, <cluster>, and <action> with proper entries.  I have no idea what this program does, so you'll have to elaborate more, but your command should look something like this:
```
/usr/bin/pg_ctlcluster 1.10 25 start
```
Again, I have no idea what the program does, or if those are valid numbers and commands, I just made something up.  See the documentation for the program for more meaningful info.

---

### Post by itisgood on 2006-09-27
thank u guys, 

ye, for the pg_ctlcluster, i think i gato read some description files,cuz neither do i know what is cluster,version..lol.

all i know is it is for the postgresql to control the cluster.and i want to start the psql..

---

