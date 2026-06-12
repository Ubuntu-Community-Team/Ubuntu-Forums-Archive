---
title: "bash script convert only files to uppercase"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by chelfc on 2008-02-22
Hi guys, I've written a bash script that I am trying to get to convert all files (not directories) in the same folder to uppercase.



how would I convert only files and not directories, and also, I assume the -i after the mv command will make it so that the original sh file isn't overwritten?

Thanks

---

### Post by chelfc on 2008-02-22
no one can help me?

---

### Post by y-lee on 2008-02-22
I modified a script  I found in the  [the Advanced Bash&#8722;Scripting Guide]("http://tldp.org/LDP/abs/html/"). It converts to uppercase all files found in the current directory.

```

#!/bin/bash
#
# Changes every filename in working directory to all uppercase.
#

# Not necessary to use basename,
# since "*" won't return any file containing "/".
for filename in *    
do n=`echo "$filename/" | tr '[:lower:]' '[:upper:]'`
#                             POSIX char set notation.
#                    Slash added so that trailing newlines are not
#                    removed by command substitution.
# Variable substitution:
   n=${n%/}          # Removes trailing slash, added above, from filename.
   [[ $filename == $n ]] || mv "$filename" "$n"
                     
done
exit $?
```

hope this helps :)

**Note:** no attempt is made to prevent this scripts name from being also converted. Add that if you wish.

---

### Post by nick_h on 2008-02-22
You could also do this with a single *find* command:
```
find . -type f -execdir rename 'y/a-z/A-Z/' '{}' \;
```
This does a recursive rename.  Use the -maxdepth to limit the depth.  Use rename with a wildcard in the current directory.

---

### Post by y-lee on 2008-02-22
> **nick_h said:**
> You could also do this with a single *find* command:
```
find . -type f -execdir rename 'y/a-z/A-Z/' '{}' \;
```
This does a recursive rename.  Use the -maxdepth to limit the depth.  Use rename with a wildcard in the current directory.


Hey that's a good one, I'm still trying to learn the ins and outs of linux :)

I like that tho that is cool, thanks :popcorn:

---

### Post by chelfc on 2008-02-23
> **nick_h said:**
> You could also do this with a single *find* command:
```
find . -type f -execdir rename 'y/a-z/A-Z/' '{}' \;
```
This does a recursive rename.  Use the -maxdepth to limit the depth.  Use rename with a wildcard in the current directory.

thanks for your help guys, how do I use the -maxdepth argument? and can you explain what the -execdir and the {} does? I can't get onto a linux machine at the moment.

---

### Post by y-lee on 2008-02-23
> thanks for your help guys, how do I use the -maxdepth argument? and can you explain what the -execdir and the {} does? I can't get onto a linux machine at the moment.

For information on find

```
man find
```

hit **q **to exit man space bar **page up** or **page down** or arrow keys to move around.

From the man pages:

> -exec command ;
              Execute  command;  true  if 0 status is returned.  All following
              arguments to find are taken to be arguments to the command until
              an  argument  consisting of ‘;’ is encountered.  The string ‘{}’
              is replaced by the current file name being processed  everywhere
              it occurs in the arguments to the command, not just in arguments
              where it is alone, as in some versions of find.  Both  of  these
              constructions might need to be escaped (with a ‘\’) or quoted to
              protect them from expansion by the shell.

>  -execdir command {} 
              Like -exec, but the specified command is run from the  subdirec-
              tory  containing  the  matched  file,  which is not normally the
              directory in which you started find.  This a  much  more  secure
              method  for invoking commands, as it avoids race conditions 
              during resolution of the paths to the matched files.

To use with maxdepth:

```
find . -maxdepth 1 -type f -execdir rename 'y/a-z/A-Z/' '{}' \;
```

---

### Post by nick_h on 2008-02-23
The *find* command works recursively.  If you want it to only search down 2 levels in the driectory structure, for example, you could use *-maxdepth 2*.  -execdir executes the following command for each file found in the directory containing the file.  The {} is substituted with the name of each file.

See the manual page for more detail:
```
man find
```

---

