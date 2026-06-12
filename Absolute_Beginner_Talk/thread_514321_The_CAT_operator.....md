---
title: "The CAT operator...."
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by blkhatpersian on 2007-07-31
hey everyone, how's it going? I know this is the third question I've had in three days, but I'm just beginning so the help I've gotten is amazing.

My question deals with the 'cat operator'.  I know it can be used to combine files and such, but the main feature that intriguied me was how it can get lists of data then put it into a file.


cat > filename

I've reached one problem though....ending the cat. a lot of my co-workers(i'm an intern) have told me ctrl + c, but that only works outside of a script.:(

So is there a way in the cat syntax that I can tell it to stop when a user inputs a certain word such as end while the command runs in a script?

Thanks,

blkhatpersian

---

### Post by blkhatpersian on 2007-07-31
nm, I foudn ctrl + d was the better command to put because it copied. Now I don't want to start a new thread, but I hope someone looks at this and answers another question for me.

I have  a problem when I run this in a script:

set number = 1
echo $number
1
set number = $number + 1

I used to do this all the time in c++ in high school so I'm confused on why it is not working

blkhatpersian

---

### Post by asmoore82 on 2007-07-31
YES!!

the output redirectors |<><<>>& are a feature of BASH ... the default shell on Linux systems
BASH itself is like its own little User Interface, Operating System and Programming Language
in a tidy little completely text-based package :KS

it seems like you already know '>' but i'll run all the basics down for you:

> output to a file; NOTE that this overwrites what was already in the file
< input from a file
>> append to a file: like '>' but safer!
<< this is called a 'here-document' - one of the more obscure shell features and
maybe what you are looking for ...
```

~$ cat << END_ASM
> this
> won't ever
> stop
> until I say END_ASM
> and END_ASM alone
> 
> END_ASM
this
won't ever
stop
until I say END_ASM
and END_ASM alone
```

NOTE that 'cat' did not reprint the final 'END_ASM' because
that was the stop label intercepted by the shell :D

P.S.

CTRL+C = Kill
CTRL+D = End of File
CTRL+S = Terminal Stop - A "PAUSE" BUTTON
CTRL+R = Terminal Resume - UNPAUSE
CTRL+Z = Stop Signal - PAUSE with a new PROMT!!
    the BASH Shell BUILTIN command **fg** will resume the process in the foreground
    the BASH Shell BUILTIN command **bg** will do the same in the background

---

### Post by asmoore82 on 2007-07-31
> **blkhatpersian said:**
> nm, I foudn ctrl + d was the better command to put because it copied. Now I don't want to start a new thread, but I hope someone looks at this and answers another question for me.

I have  a problem when I run this in a script:

set number = 1
echo $number
1
set number = $number + 1

I used to do this all the time in c++ in high school so I'm confused on why it is not working

blkhatpersian

C++ is a high-level language that is compiled and for number crunching
BASH is an interactive scripting language that excels at text crunching ...
'set' is a SHELL BUILTIN that only needs to be used when you are changing BASH's private options ...

try this....
```

asmoore@asmoore-laptop:~$ num=1
asmoore@asmoore-laptop:~$ echo $num
1
asmoore@asmoore-laptop:~$ num=$(( num + 1 ))
asmoore@asmoore-laptop:~$ echo $num
2
asmoore@asmoore-laptop:~$ echo $(( num++ ))
2
asmoore@asmoore-laptop:~$ echo $num
3
```

because BASH is an interactive scripting language it is sort of a hassle to make it do
lowly arithmatic but anything inside of "$(( ... ))" is interpreted pretty much exactly like C++ math operators

---

### Post by asmoore82 on 2007-07-31
The POWER of BASH's text manipulation ...
```

asmoore@asmoore-laptop:~$ echo $PWD
/home/asmoore
asmoore@asmoore-laptop:~$ cd Desktop
asmoore@asmoore-laptop:~/Desktop$ echo $PWD
/home/asmoore/Desktop
asmoore@asmoore-laptop:~/Desktop$ echo ${PWD#*/}
home/asmoore/Desktop
asmoore@asmoore-laptop:~/Desktop$ echo ${PWD##*/}
Desktop
asmoore@asmoore-laptop:~/Desktop$ echo ${PWD//\// -> }
-> home -> asmoore -> Desktop
asmoore@asmoore-laptop:~/Desktop$ echo $PATH
/home/asmoore/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
asmoore@asmoore-laptop:~/Desktop$ echo -e "${PATH//:/\\n}"
/home/asmoore/bin
/usr/local/sbin
/usr/local/bin
/usr/sbin
/usr/bin
/sbin
/bin
/usr/games

```

---

### Post by blkhatpersian on 2007-08-01
AWESOME! Thanks a lot for the help, I appreciate it...

but i have one more question if you don't mind heh.


I'm designing a chmod utility that will let you change mutliple files in succession based off an input cat list.

for example, the prompt will say, "Which files you want to change?"
 
then a cat operator runs and takes the data, then with a foreach loop reads each line, and individually asks for the chmod command.

The problem is sometimes one file or rather line has an error because it does not exist or a typo. Is there a way I can tell the script to display "error: file not found" and simply go on to the next file?


Thanks,

blkhatpersian

---

### Post by asmoore82 on 2007-08-01
I am confused as to what you are trying to accomplish...

the chmod command already can take an arbitrary number of filenames on the command line.

---

### Post by blkhatpersian on 2007-08-01
wow....I hadn't come across that fact. Thanks for telling me, I can stop wasting time on it now heh.


take care,

blkhatpersian

---

### Post by asmoore82 on 2007-08-01
> **blkhatpersian said:**
> wow....I hadn't come across that fact. Thanks for telling me, I can stop wasting time on it now heh.


take care,

blkhatpersian

you can read a ***manpage*** when you come accross new commands or
when just want to know more advanced stuff about old commands ...

```
~ $ man *<any command name>*
```

press <slash>[/] to search for words in the manpage and
press [q] to quit the man program

---

