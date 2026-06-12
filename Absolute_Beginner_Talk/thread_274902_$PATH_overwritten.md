---
title: "$PATH overwritten"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by mottooo on 2006-10-10
Hi,

I've only been using linux for 2 weeks now. but i think i'm getting along well. praise the lord for repositories. anyhow.

I tried to install this program [visual route (vr10)], and in the installation notes it said 

  Make sure the current directory ('.') is in the PATH environment   
  variable.

	# PATH=$PATH:.; export PATH

the following ensued...

  PATH=$PATH
  PATH=./home/furri/vr10

my buffer has gone too far back or i would have pasted the responses. I typed those two lines.. Below is what I tried to do to fix it

  furri@myn3xtop:~/vr10$ java vr
  bash: java: command not found
  furri@myn3xtop:~/vr10$ ls
  bash: ls: command not found
  furri@myn3xtop:~/vr10$ PATH=$PATH
  furri@myn3xtop:~/vr10$ java vr
  bash: java: command not found
  furri@myn3xtop:~$ PATH=./usr/bin
  furri@myn3xtop:~$ ls
  bash: ls: command not found
  furri@myn3xtop:~$ aptitude search gloria
  bash: aptitude: command not found
  furri@myn3xtop:~$ PATH=/usr/bin
  furri@myn3xtop:~$ aptitude search gloria

At this point, aptitude worked. Then I did
  
  furri@myn3xtop:~$ ls
  bash: ls: command not found
  furri@myn3xtop:~$ dir
  bash: dir: command not found

didnt work.. SO

  furri@myn3xtop:~$ PATH=/bin
  furri@myn3xtop:~$ dir
  ABC-Linux-V.2.4.3

WORKED! So i back tracked, cuz before aptitude wasnt working and ls was, and now the opposite. Case in point ladies and gentlemen, 

  furri@myn3xtop:~$ aptitude search avg
  bash: aptitude: command not found
  furri@myn3xtop:~$ gedit .bash_profile
  bash: gedit: command not found

a) Can somebody please advise what the default .bash_profile should look like ?

b) Explain how I can add multiple directories to the PATH variable?

c) And if you're really nice, explain the difference between PATH and $PATH.


Thanks for reading my 1000 word essay above.

My current .bash_profile looks like this, after reading a post here

  # ~/.bash_profile: executed by bash(1) for login shells.
  # see /usr/share/doc/bash/examples/startup-files for examples.
  # the files are located in the bash-doc package.

  # the default umask is set in /etc/login.defs
  #umask 022

  # include .bashrc if it exists
  if [ -f ~/.bashrc ]; then
      . ~/.bashrc
  fi

  # set PATH so it includes user's private bin if it exists

  PATH=$PATH:$HOME/bin:/sbin:/usr/sbin

  PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:/usr/lib/pkgconfig


  export PKG_CONFIG_PATH
  export PATH
  unset USERNAME


thanks a lot!

---

### Post by ubuntuuser on 2006-10-10
A = $B means: "Take a variable (container) with the name of A and fill it with the content of B."

So PATH=$PATH does not change anything, it sets the content of PATH to the content of PATH (sounds silly, right?). The trick is that when you use something like    PATH=$PATH:$HOME/bin:/sbin:/usr/sbin, you take a variable named PATH and set its content to everything that is already in PATH, plus ~/bin, /sbin and /usr/sbin. 

So $PATH refers to the content of PATH, while PATH is the name. If you have some programming experience, this is just like a=a+1.

The readme told you to do this ```
# PATH=$PATH:.; export PATH
```This adds . (the current directory) to PATH. To inform your system of the changes you need to export PATH again.

I can't help you with the default .bash_profile, not at a linux box right now, but yours looks ok to me.

---

### Post by mottooo on 2006-10-10
bredren,

I did the following:

  furri@myn3xtop:~$ PATH=$PATH:$HOME/bin:/usr/bin:/sbin:/bin/usr

and most of my commands are working now.

Thanks very much for the tut.

---

### Post by maaronB on 2006-10-10
Are you saying that you add this

```
PATH=$PATH
PATH=./home/furri/vr10

```
to youre bash_profile?

If that is what happened then I can explain the problem.

PATH is an enviorment variable.  
It contains a list of all the places that a command might be found.  Every time you type a command into a terminal.  The computer searches the locations pointed to by PATH for a program/script with that name.

PATH is the name of the variable.
$PATH is the value stored in the variable

So if I type 
echo PATH
it returns 
PATH

but if I type echo $PATH
it returns something like,
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

The PATH variable is actually set somewhere in the murky depths of the init processs.

But you can modify it in your ~.bash_profile or ~.bashrc
This looks like what you have done.

by adding this line
```

PATH=./home/furri/vr10

```

you have overwritten the default PATH with ./home/furri/vr10
This means the only place your computer checks for programs is in ./home/furri/vr10.  Since no ls, dir, or gedit program is at that location you can't edit your files.

To fix it you should just be able to change 
```

this
PATH=./home/furri/vr10
to
export PATH=$PATH:./home/furri/vr10

```

but because you asked I have included my ~./bash_profile
```

# ~/.bash_profile: executed by bash(1) for login shells.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/login.defs
#umask 022

# include .bashrc if it exists
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

```

---

### Post by ubuntuuser on 2006-10-10
> **maaronB said:**
> 
```

this
PATH=./home/furri/vr10
to
export PATH=$PATH:./home/furri/vr10

```
I didn't notice it first, but it has to be /home/furri/vr10, not ./home/furri/vr10 (notice the missing dot ).

---

### Post by mottooo on 2006-10-11
thanks to both of you.

i'm up and running again. and happy to be still learning new stuff as i proceed.

Re,

Furri

---

