---
title: "Moving files Script Help"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by kspades on 2007-06-01
Hey guys, Im trying to write a script (can be shell, perl, whatever) that looks through a buch of sub-directories and find files, then appends the directory name to the file then move all the files to another directory. 

so for example I have 2 directories with files

dir1\file1.out
dir1\filename2.out
dir2\testfile.out

the script would find all those files and rename them to dir1-fine1.out. dir1-filename2.out, dir2-testfile.out then move all those files to a single directory called \output.

I am new at this and have no idea where to even begin, could you guys help?

thanks

---

### Post by eljalill on 2007-06-02
While not being good a writing scripts myself, 
I still found this page a good starting point and a lot of help:
[http://linuxcommand.org/wss0010.php](http://linuxcommand.org/wss0010.php)

Cheers

---

### Post by Skrynesaver on 2007-06-02
presupposing the existence of the output directory in the current directory, the following should achieve what you want
```

for x in $*;do
if [ -d $x ] ;then
        for i in $(find $x -type f);do
                mv $i output/$(dirname $i)$(basename $i)
        done
else
        echo "$0 should only be called on directories"
fi
done

```

in the case you outlined if the above is saved as mover.sh the call it as follows
```

./mover.sh dir1 dir2

```
Note that it will parse all subdirectories and only move ordinary files.
Hope this does the job for you.

---

### Post by kspades on 2007-06-02
> **Skrynesaver said:**
> presupposing the existence of the output directory in the current directory, the following should achieve what you want
```

for x in $*;do
if [ -d $x ] ;then
        for i in $(find $x -type f);do
                mv $i output/$(dirname $i)$(basename $i)
        done
else
        echo "$0 should only be called on directories"
fi
done

```

in the case you outlined if the above is saved as mover.sh the call it as follows
```

./mover.sh dir1 dir2

```
Note that it will parse all subdirectories and only move ordinary files.
Hope this does the job for you.


Thanks for your reply, 
is there anyway I could do the script so I dont have to specify the preexisting directories? the directories will change over time

---

### Post by 56phil on 2007-06-02
Here's my solution in python.

```

#!/usr/bin/env python
import os
import sys
import shutil


def do_dir(src, dst):
    cnt = 0
    src_len = len(src) + 1
    slash = '/'
    dash = '-'
    for root, dirs, files in os.walk(src):          # recurse source directory
        for file in files:
            src_path = os.path.join(root, file)
            pth = root[src_len:]
            pth = pth.replace(slash,dash)
            if len(pth) > 0: 
                pth += dash
            dst_path = os.path.join(dst, pth + file)
            shutil.move(src_path, dst_path)
            cnt += 1
    return cnt


if __name__ == '__main__':
    src_dir = os.getcwd()
    dst_dir = sys.argv[1]
    
    if os.path.exists(dst_dir) == False:            # check destination dir
        os.mkdir(dst_dir)
        os.chmod(dst_dir, 0744)
        print 'Created directory ', dst_dir
    
    num_moved = do_dir(src_dir, dst_dir)
    print 'Moved', num_moved, 'files.'

```

To use it, navigate to the top directory you want to move. and execute the script.  

It accepts one argument which is the full path of the destination (i.e. /home/<user>/<destination>)


Hope this helps.
---

p.s. Have you looked into tar? It looks like that might be a more effective solution.

---

### Post by Skrynesaver on 2007-06-02
As it stands it will process the directories listed into the output directory.
If you wish to make the output directory variable you will have to write an argument processing function, thus we could add a the following to the head of the script, (now called moveTo.sh ;) )
```

#!/bin/bash
output=$1
shift
if [ ! -d $output ]; then
        mkdir $output
fi
echo $output
for x in $*;do
if [ -d  $x ] ;then
        for i in $(find $x -type f);do
                base=$(dirname $i)
                base=$(echo $base|tr '[/]' '[\-]'
                mv $i $output/$base-$(basename $i)
        done
else
        exit 1
fi
done


```

now if called as follows
```

moveTo.sh newout toplevel1 toplevel2

```
The ordinary files of toplevel1 and toplevel2 and their subdirectories will be put in the directory newout withe their paths as prefixes.

---

### Post by kspades on 2007-06-02
> **Skrynesaver said:**
> As it stands it will process the directories listed into the output directory.
If you wish to make the output directory variable you will have to write an argument processing function, thus we could add a the following to the head of the script, (now called moveTo.sh ;) )
```

#!/bin/bash
output=$1
shift
if [ ! -d $output ]; then
        mkdir $output
fi
echo $output
for x in $*;do
if [ -d  $x ] ;then
        for i in $(find $x -type f);do
                base=$(dirname $i)
                base=$(echo $base|tr '[/]' '[\-]'
                mv $i $output/$base-$(basename $i)
        done
else
        exit 1
fi
done


```

now if called as follows
```

moveTo.sh newout toplevel1 toplevel2

```
The ordinary files of toplevel1 and toplevel2 and their subdirectories will be put in the directory newout withe their paths as prefixes.


thanks but I dont think I explained it right.
I'd like to just run 
move.sh /path/to/sub-folders
I dont want to specify the directories on the command line.

---

### Post by Skrynesaver on 2007-06-02
OK then try this
if [ ! -d output ];then
   mkdir output
fi
if [ -d  $1 ] ;then
        for i in $(find $x -type f);do
                base=$(dirname $i)
                base=$(echo $base|tr '[/]' '[\-]'
                mv $i $output/$base-$(basename $i)
        done
else
        exit 1
fi
done
Should add the called directory and all its subdirectory's  files to the output directory.

---

