---
title: "zsh saved my life, could bash do this?"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by jordanmthomas on 2007-09-18
Ok, so I have just finished up a project for my distributed computing class that has been a real pain.  I was looking at the files in the directory and noticed a few that ended in ~.  I knew what these were from and that I didn't need them (I just haven't turned off the auto-backup thing in kdevelop, no biggie).  So, I do my usual task of
```
 rm *~
``` to clean them up.

As my finger slides over to the return key, I am pretty much just relieved I'm going to be able to tar this stupid thing up and get it out of my life.  As I am pressing the key I notice I never actually hit the ~ key.  NOOOOOOOOOOOOO!   Luckily (apparently) I use zsh and it asked if I was sure I wanted to delete *.  I sighed a sigh of great relief.

Now, I know bash would have just gone off and deleted them.  I also know I could alias rm to rm -i, but that is annoying to me since I don't mess up *that* often and I do a good bit of deleting.  

So, after my lengthy description, here's the meat of the question:
**can bash detect a rm * and stop it to make sure that's what you want?  I'd rather not alias rm to rm -i since it's annoying.  I can live with rm -I I suppose, but maybe there's something better still.**

I'd like to know because I don't always have the option of zsh everywhere I go and I'd like to set up bash to do this since it is pretty much available everywhere.  Thanks for reading this if you did and I look forward to your suggestions.

---

### Post by punx45 on 2007-09-18
according to the man page for rm, -f overrides -i, so maybe you can set the alias to rm -i for everyday use, and when you want to do a big delete and not be annoyed you can issue rm -f.

---

### Post by jordanmthomas on 2007-09-18
Unfortunately, it's annoying for the small things.  I know, I'm picky.  :)

I suppose I could just use
```
rm -I 
```
and it wouldn't be too annoying when I'm away from my precious zsh.

Thanks for the suggestion, it made me decide that I can probably deal with it.  I don't know why it did, but I think I've changed my mind now.

**edit**
God, my internet is slow.  It took me like 15 minutes to read your response and reply.

---

### Post by asmoore82 on 2007-09-18
I need more details about the situation...

Are you *sure* it was zsh that asked for confirmation and not the 'rm' command itself?

What if you ran another 'rm' command in the exact same zsh environment, would it also ask?

---

### Post by dwhitney67 on 2007-09-18
You can add these "functions" to your .bashrc (or other sourced file):

```

#!/bin/bash

del()
{
  if [ $# = 0 ]; then exit; fi
  mkdir -p ~/.trash
  mv $* ~/.trash
}

delall()
{
  mkdir -p ~/.trash
  FILES=`ls *`
  for file in $FILES
  do
        del $file
  done
}

deltrash()
{
  rm -rf ~/.trash/*
}

```

Examples of usage of 'del':

[FONT="Courier New"][INDENT]del myFile_1.txt
del myFile_*.txt
del myFile*
del file1 file2
del myFolder[/INDENT][/FONT]
The following command will _**not**_ work because only the first file listed in the directory will get "deleted".  Use 'delall' instead.  Note that 'delall' does not examine any given command line args.
[FONT="Courier New"]
[INDENT]del *[/INDENT][/FONT]
Instead use:
[INDENT][FONT="Courier New"]delall[/FONT][/INDENT]
To permanently erase "deleted" files and folders:
[INDENT][FONT="Courier New"]deltrash[/FONT][/INDENT]
Of course these functions are kludges.  Probably a more knowledgeable bash-know-it-all can think of something better.

---

### Post by asmoore82 on 2007-09-18
Whoa!! .. you've got major bugs in your code there ...

1. Gnome uses a "~/.Trash" folder with an uppercase "T"
why don't we use it too since it is more likely to already exist.

2. quotation marks are very important in preventing all sorts of
unwanted "extra features"[bugs] in shell scripts;
when in doubt, encase in quotation marks

3. the bracket test is really designed for strings and not numbers;
whenever you want to compare numeric values you should use the
``-eq'' test instead of the ``='' string comparison.

4. just because we have ``mkdir'' our trashcan; we cannot be 100% sure
that it did not already exist as a regular file/fifo, better to check and be
100% sure, before "deleting" files for the user.

5. and [SIZE=3]**most importantly**[/SIZE], the variable ``$*'' does ***_not_*** do what
you think it does; particularly when **filenames with spaces** come along.

the corrected version of the del function would look like this:
```
del()
{
  if [ "$#" -eq "0" ]; then
    exit;
  fi

  mkdir -p ~/.Trash
  if [ ! -d "~/.Trash" ]; then
    echo 'error: nothing deleted; check your ~/.Trash.' 1>&2
    exit 127;
  fi

  mv "$@" ~/.Trash
}
```

Likewise, I am fairly certain that there are major problems with your
delall() function when **filenames with spaces** are involved.

that takes care of "bugs" ~ problems hidden in the code...

now what about design flaws ~ problems that started before the code was written:
What happens if someone wants to ``del'' or ``delall'' files off of a usb or flash drive ??

Sorry if I come on too strong; but all of these bugs and issues that I *quickly*
recognized are meant to *emphasize* why we should follow suit with good
time-tested UNIX admin practices... If you want to use the command line, you
should get comfortable with the pre-existing behaviour of common commands
such as ``rm'' .... aliasing ``rm'' to ``rm -i'' is just an all around good idea.

---

### Post by jordanmthomas on 2007-09-19
> **asmoore82 said:**
> I need more details about the situation...

Are you *sure* it was zsh that asked for confirmation and not the 'rm' command itself?

What if you ran another 'rm' command in the exact same zsh environment, would it also ask?

Yes, it was zsh (and nothing in my .zshrc does it).  I did it in bash and it just removed.
I did it on a Mac to test and it did the same thing in zsh.  The question is worded differently than rm -i (or rm -I) would word it.

dwhitney:
   What you've proposed is a good idea in theory, but I will be rewriting what you have there (no offense).
    (edit:  asmoore seems to agree ;)  )

Thanks for the help guys.

(edit2:  I'm very happy.  This is probably my first thread people have really tried to help me with.  Usually, my threads stagnate and nobody helps...kinda a letdown sometimes.)

---

### Post by dwhitney67 on 2007-09-19
> **jordanmthomas said:**
> 
dwhitney:
   What you've proposed is a good idea in theory, but I will be rewriting what you have there (no offense).
    (edit:  asmoore seems to agree ;)  )

Just so you know, I personally do not use those bash functions.  I just threw them up on the web as a possible solution.  I am not a bash expert, nor do I care to be one.

---

### Post by jordanmthomas on 2007-09-19
Alright then, you are forgiven...**this** time.

Just playing, I certainly appreciate the help and your stuff would probably work alright some of the time at least.  :)

---

### Post by asmoore82 on 2007-09-19
I acutally had to write a test script to remember when to use $* or $@ ...
a polished version of that script and running it...

```

**asmoore@asmoore-laptop:~$** ls -l ./bin/test 
-rwxr-xr-x 1 asmoore asmoore 261 2007-09-19 00:25 ./bin/test
**asmoore@asmoore-laptop:~$** cat ./bin/test 
#!/bin/bash

argcheck()
{
        echo '$* test:'
        for args in $*
        do
                echo -n ' ->' "$args"
        done
        echo ""

        echo '"$*" test:'
        for args in "$*"
        do
                echo -n ' ->' "$args"
        done
        echo ""

        echo '"$@" test:'
        for args in "$@"
        do
                echo -n ' ->' "$args"
        done
        echo ""

        echo "tests complete."
}

argcheck "arg1" "arg2" "arg3 part1 part2" "arg4"

**asmoore@asmoore-laptop:~$** ./bin/test 
$* test:
 -> arg1 -> arg2 -> arg3 -> part1 -> part2 -> arg4
"$*" test:
 -> arg1 arg2 arg3 part1 part2 arg4
"$@" test:
 -> arg1 -> arg2 -> arg3 part1 part2 -> arg4
tests complete.

```

^^ only "$@" behaves as one would expect for everyday use.

---

