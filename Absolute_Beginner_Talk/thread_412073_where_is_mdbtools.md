---
title: "where is mdbtools?"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by sh4d3z on 2007-04-17
i have been told to install mdbtools for looking at mdb file and porting it to mysql
that went smoothly with no problem
my only problem w/ it is i don't know where i am supposed to open it, i've looked all over for it in the application menu, also tried typing it's name 'mdbtools' on the cli 
i really need to be able to view these for this class i'm taking

---

### Post by Skrynesaver on 2007-04-17
From the command line type
```
 sudo apt-get install mdbtools
```you will then have the commands at your disposal.
save the following as mdb-explode and make it executable
```

#! /bin/bash
mkdir $(echo $1|awk -F"." 'print $1').csvs
for i in $(mdb-tables $1);do
   mdb-export $i $(echo $1|awk -F '.' 'print $1').csvs/$i.csv
done

```This will give you all of the tables as comma separated values in a new directory. I have found this really useful when integrating apps, best of luck

---

### Post by sh4d3z on 2007-04-18
ahhh, yes thank you very much this is starting to make more sence
my problem was mdbtools wasn't a command rather it is more like a suite right
thanx for the script too

---

