---
title: "setting temporary path in shell"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by bcs on 2007-01-15
Hello,
I seem to remember reading somewhere that you can set temporary path(s) in the shell, so you don't need to type full pathnames...anyone know how to do that??

---

### Post by mlissner on 2007-01-16
I assume you're referring to the PATH variable, which indicates the order of directories the terminal looks for utilities. 

Hope that's the case. If so, I'll walk you through it:

Start by looking at its current value by doing this:
```
echo $PATH
```
I got the following output from that:
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/home/mlissner/bin/:.

```

You'll see that the PATH variable is a series of directories separated by colons. Now, since the PATH variable is just a variable afterall, the trick is to modify it, and I assume that you want to add another couple of variables onto the end of it. To do this, run this command in the terminal:
```
PATH=$PATH:directory_you_want_added:next_one:next_one
```
That should work until you close the terminal, but once you do, the value of the PATH variable that you just put in will be lost.

To change it permanently, you need to edit a file in your home directory called .bashrc, which contains a number of things that are set/run every time you start up a terminal (but not while it is running). 

Do this: 
```
gedit .bashrc
```
Go to the VERY bottom, and add in the PATH=... line from above, save and quit. Close the terminal, open it, and everything should work hence forth. 

Remember that .bashrc file. It's a dream when you want to make yourself shortcuts, save little functions into your terminal, etc. 

Let me know how it goes.

---

### Post by bcs on 2007-01-16
Thanks, mlissner.  Worked like a charm!  I  had just wanted to temporarily add the path of a script to save me from having to repeatadly type the full path...is there anything else you use temporary path for?  What kind of functions have you added to .bashrc?  This would only work with scripts, not with looking at text files, right?  It doesn't seem to work when I do  "vi filename_of_file_in_path".

---

### Post by ComplexNumber on 2007-01-16
you also need to export the PATH so that it applies to the duration of the desktop session using 'export PATH' at the very end.

---

### Post by bodhi.zazen on 2007-01-16
> **ComplexNumber said:**
> you also need to export the PATH so that it applies to the duration of the desktop session using 'export PATH' at the very end.

.... in .bashrc

PATH=$PATH:directory_you_want_added:next_one:next_one
export PATH

---

### Post by mlissner on 2007-01-17
Well, actually at the moment I don't have too much in there:

```
###MY ADDITIONS##
#Add directories to the path variable.
PATH=$PATH:~/bin/:.
#Add some aliases
alias thunderbird=mozilla-thunderbird
alias bye=exit
alias shred='shred -vuz'
alias sysmon='gnome-system-monitor'

```

I used to have some functions in there, but my harddrive crashed not too long ago and I haven't built it back up yet.

Here's a post on the subject though: [http://www.ubuntuforums.org/showthread.php?p=2024291#post2024291](http://www.ubuntuforums.org/showthread.php?p=2024291#post2024291)

See what we get I suppose.

---

### Post by Unknowndeepness on 2007-01-17
```

alias mydir=/usr/bin
cd mydir

```

mabie? (:

---

### Post by bcs on 2007-01-17
Thanks!  I didn't realize that vi shortcuts/functions could be controlled like that.

---

### Post by mlissner on 2007-01-17
> **Unknowndeepness said:**
> ```

alias mydir=/usr/bin
cd mydir

```

mabie? (:

Nah, that won't work because aliases aren't really all that flexible. You're on the right track though. If you do:
```
mydir='/usr/bin'
cd mydir
```

It'll work...

---

