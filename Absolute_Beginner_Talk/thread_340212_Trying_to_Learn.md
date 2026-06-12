---
title: "Trying to Learn"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2007-01-16
Trying to make a simple alias for rm, to send the file to the .Trash instead of zapping it:  Both
```
alias rm='mv $1 ~/.Trash'         and
alias rm='mv /.Trash $1'            then 
rm test
```
produce a message when run, something like     mv: cannot overwrite non-directory `test' with directory `/home/buck/.Trash'
The only way I could make it work is
```
alias rm='mv -t ~/.Trash $1'
```

I can't get it to work at all going the other way, to restore a file from the .Trash to the current directory:
```
buck@argos:~$ alias und='mv -t . ~/.Trash/$1'
buck@argos:~$ und test
mv: `/home/buck/.Trash/' and `./.Trash' are the same file
mv: cannot stat `test': No such file or directory
buck@argos:~$ alias und='mv ~/.Trash/$1 .'
buck@argos:~$ und test
mv: target `test' is not a directory
```
But when I put it in a one-line shell script it works fine:
```
#! /bin/bash
#! /bin/bash
mv /home/buck/.Trash/$1 .
```
I'd like to understand what's going on here.  Also, is the $1 the correct variable name to use for the command argument?  Are there others that would work?

Thanks,
Buck

---

### Post by goatflyer on 2007-01-16
$1 is the name of the first command line argument in bash (and sh and others)

$* means all the arguments.  So does $@ but with a difference.

('man bash' is a long, but fairly complete read -- and often much much more than you want to know, really, but eventually you do learn the shell grammar)

'alias' does not take arguments, it is used just to replace the command name part, so $1 shouldn't work there at all I think


Anyway,
```

alias rm='mv -t ~/.Trash/'

```

will do what you want --- mostly --- but even this will fail if you already 'deleted' a file with the same name and the file still exists in the ~/.Trash directory

Better with the script so you can add the necessary ifs

---

### Post by Buck2348 on 2007-01-16
That explains it--just what I wanted to know.  Thank you very much.

Regards,
Buck

---

