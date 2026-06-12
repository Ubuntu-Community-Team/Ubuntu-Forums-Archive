---
title: "Command to delete all files except last three"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by abcuser on 2007-04-12
Hi,
I need to write a script file (.sh) to delete all files in directory except last three ordered by file name descending.

Sample:
In my directory are for example the following files:

aaa20070101.log
aaa20070102.log
aaa20070202.log
aaa20070204.log
aaa20070302.log

I should preserver files: 
aaa20070202.log
aaa20070204.log
aaa20070302.log
because they are last three files sorted descending. All other files should be deleted.

Any idea?

Thanks,
Abcuser

---

### Post by spin2cool on 2007-04-12
I'm sure that this can be done more cleanly, but here's one way that should work:

```
#!/bin/bash

ls -ct1 >temp.txt
lines=`wc temp.txt | awk '{ print $1 }'`
keep=3
toremove=$(expr $lines - $keep)
tail -$toremove temp.txt>temp2.txt
cat temp2.txt | while read line; 
do 
echo rm "${line}"; 
done

#remove temp files
rm temp.txt
rm temp2.txt
```

Right now, it just prints out the names of the files to be deleted, so you can test it - remove the "echo" to make it do the deletion

---

### Post by Arndt on 2007-04-12
> **abcuser said:**
> Hi,
I need to write a script file (.sh) to delete all files in directory except last three ordered by file name descending.

Sample:
In my directory are for example the following files:

aaa20070101.log
aaa20070102.log
aaa20070202.log
aaa20070204.log
aaa20070302.log

I should preserver files: 
aaa20070202.log
aaa20070204.log
aaa20070302.log
because they are last three files sorted descending. All other files should be deleted.

Any idea?

Thanks,
Abcuser

I suggest copying (or linking) the files you want to keep, to some other location, and then delete all the files, rather than calculate a list of files to remove. If I did it manually, I would do

```
$ mkdir keep
$ cp -p aaa20070202.log aaa20070204.log aaa20070302.log keep
$ rm *
rm: cannot remove `keep': Is a directory
$ mv keep/* .
$ rmdir keep
```

---

### Post by abcuser on 2007-04-12
Arndt,
the file names to keep are constantly changing, so I don't know which exactly file to keep. The only thing I know is "I need to keep last 3 files sorted descending".
Thanks,
Abcuser

---

### Post by abcuser on 2007-04-12
> **spin2cool said:**
> I'm sure that this can be done more cleanly, but here's one way that should work:

```
#!/bin/bash

ls -ct1 >temp.txt
lines=`wc temp.txt | awk '{ print $1 }'`
keep=3
toremove=$(expr $lines - $keep)
tail -$toremove temp.txt>temp2.txt
cat temp2.txt | while read line; 
do 
echo rm "${line}"; 
done

#remove temp files
rm temp.txt
rm temp2.txt
```

Right now, it just prints out the names of the files to be deleted, so you can test it - remove the "echo" to make it do the deletion

Hi,
I have modified your script, which was excellent starting point. Thanks a lot.

```

#!/bin/bash

VarDir=/home/db2inst1/x
VarNumKeep=3

VarNumAll=`ls -ct1 $VarDir | wc -l`
VarNumRemove=$(expr $VarNumAll - $VarNumKeep)

ls -ct1 $VarDir | head -$VarNumRemove | while read VarLine;

do
rm "$VarDir/${VarLine}";
done
```

I just added some variables, removed "> temp.txt" commands with pipes and add "directory to delete from". I also renamed variables for easy to read.

Thanks a lot,
Abcuser

---

### Post by spin2cool on 2007-04-12
Yeah, I know the temp files were ugly, but I did it off the top of my head.  Glad it helped.

---

