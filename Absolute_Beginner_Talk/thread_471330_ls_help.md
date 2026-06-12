---
title: "ls help"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by oldcpu on 2007-06-11
How do I get `ls` to print along the size too?  I can only get it to print the block size.  If I used `ls -l`, it would print other extra things too; I just want the file name and size.

I would like to `ls` it by type.  How would I do that?  I am not asking to display a certain file, but how do I get `ls` to arrange it by type first, then alphabetically order.

You know how listing a long list of files would get truncated off the console screen?  How would I get it to list only what fits in the screen and require me to hit Enter or any key for the rest?

---

### Post by RedSquirrel on 2007-06-11
Have a look at the man page for ls:

```
 man ls
```filename and size

```
 ls -sh
```to sort by type (suffix):

```
ls -X
```for size and type:

```
ls -Xhs
```to only show one screenful at a time, use **more**, e.g.:

```
 ls -l | more
```

press SPACEBAR to see the next screenful.

---

### Post by Inxsible on 2007-06-11
> **oldcpu said:**
> How do I get `ls` to print along the size too?  I can only get it to print the block size.  If I used `ls -l`, it would print other extra things too; I just want the file name and size.

I would like to `ls` it by type.  How would I do that?  I am not asking to display a certain file, but how do I get `ls` to arrange it by type first, then alphabetically order.

You know how listing a long list of files would get truncated off the console screen?  How would I get it to list only what fits in the screen and require me to hit Enter or any key for the rest?
At the terminal, enter
```
man ls
``` It will provide you with all the options available for ls. 

-s will list the size of the file
-S will sort by file size
--sort=WORD   --------Replace word by a number of options -X will sort them by file extensions.

I dont know how to show them page wise tho, but -m will fill the width of the terminal with file names. You can probably try a combination of those, to get what you want.

---

### Post by oldcpu on 2007-06-11
Ah, thanks!

I have read the manual prior to asking.  But when I tried out the functions, I only used one at a time.  I did not thought of combining them.  Thanks again!

EDIT:

A bit off topic.
```
alias ls='ls -Xhs | more'
```does not work in ~/.bashrc

Why is that?

---

### Post by RedSquirrel on 2007-06-12
lt is already set in ~/.bashrc:

```
grep ls= .bashrc
```gives

```
alias ls='ls --color=auto'
```I would recommend using something else for your new alias, e.g.:

```
alias lsm='ls -Xhs | more'
```


EDIT:

I would also recommend you follow this advice from the ~/.bashrc file

```
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

```

It's not strictly necessary, but I like to do this rather than clutter the ~/.bashrc file with a bunch of aliases. ;)

---

### Post by steve.horsley on 2007-06-12
There some aliases already defined but commented out in .bashrc. "ll" seems like agood candidate for uncommenting.

You need to log out/in again for changes in .bashrc to affect your GUI consoles.

---

### Post by oldcpu on 2007-06-12
Thanks!  Worked wonderfully.

I love how so many things in Linux can be configured to my liking.

Say, is it better to write a script if the code gets a little longer or is it okay to just write it into ~/.bash-aliases?

When piped, the ls loses its colors.  I was thinking of trying to write a script to add colors to different types of files.  Or is there an easier way that will go around the piping?

---

### Post by steve.horsley on 2007-06-13
Not sure about colours. 

I wouldn't write a script unless the command was more than one line, but that's personal choice.

---

### Post by RedSquirrel on 2007-06-14
> **oldcpu said:**
> Thanks!  Worked wonderfully.

You're welcome.


> **oldcpu said:**
>  I love how so many things in Linux can be configured to my liking.

Yes, I love that too. :)


> **oldcpu said:**
>  Say, is it better to write a script if the code gets a little longer or is it okay to just write it into ~/.bash-aliases?

You can put things wherever you want but a script might be a good idea if you need to (or choose to) use several lines.


> **oldcpu said:**
>  When piped, the ls loses its colors.  I was thinking of trying to write a script to add colors to different types of files.  Or is there an easier way that will go around the piping?

Yeah, the colour goes away as a result of the *more* command. I'm not sure how to get it back.

As an alternative to colour, you can use the '-F' option which will "classify" the entries (it appends '/' to directories, '* ' to executable files, etc.).

---

### Post by steve.horsley on 2007-06-14
I believe that ls only adds the colour codes if it's outputting to a TTY. When it's piped into another program that's not the case, which is a good job as the colour codes would confuse other programs that receive them as input.

---

