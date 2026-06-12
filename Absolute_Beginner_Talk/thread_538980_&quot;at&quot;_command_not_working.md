---
title: "&quot;at&quot; command not working"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by fredscripts on 2007-08-30
Hi There! I'm just wondering why the "at" command is not working, for example:

```
fredscripts@laptop:~$ echo konqueror ~/LinuxDoc/KubuntuDesktopGuide.pdf | at now
warning: commands will be executed using /bin/sh
job 5 at Thu Aug 30 23:04:00 2007
fredscripts@laptop:~$
```


Doesn't do anything. And the normal way:
```

fredscripts@laptop:~$ at 23:07
warning: commands will be executed using /bin/sh
at> firefox<EOT>
job 6 at Thu Aug 30 23:07:00 2007
fredscripts@laptop:~$

```

Doesn't do anything too at the hour I told.


Thank you very much for your help!

---

### Post by fredscripts on 2007-08-30
Any ideas? :( Any other command to perfom tasks like "tomorrow at 10:27 run the command *foo*"?

---

### Post by bashologist on 2007-08-30
Does this work better?
```
echo "DISPLAY=$DISPLAY konqueror ~/LinuxDoc/KubuntuDesktopGuide.pdf" | at now
```
There's some good information here: [http://en.wikipedia.org/wiki/At_(Unix)](http://en.wikipedia.org/wiki/At_(Unix))

---

### Post by fredscripts on 2007-08-30
> **bashologist said:**
> Does this work better?
```
echo "DISPLAY=$DISPLAY konqueror ~/LinuxDoc/KubuntuDesktopGuide.pdf" | at now
```
There's some good information here: [http://en.wikipedia.org/wiki/At_(Unix)](http://en.wikipedia.org/wiki/At_(Unix))


Yes! That worked! Thanks! 

But the classical way didn't work:

```
fredscripts@laptop:~$ at 00:05
warning: commands will be executed using /bin/sh
at> DISPLAY=$DISPLAY konqueror<EOT>
job 8 at Fri Aug 31 00:05:00 2007
```


Didn't do nothing at 00:05.


Anyway what's DISPLAY=$DISPLAY for? Is there any way to run the classic "at" command like in the wiki documentation you attached is shown?

Thanks!

---

### Post by fredscripts on 2007-08-30
I don't pretend to be tedious, but I'm very interested on running some commands at a specific hour on a specific day, can anyone help me with this "at" command estrange behavior?:(

Thanks!

---

### Post by spupy on 2007-08-30
When you do the "classical" way:
```
$ at now
export DISPLAY=$DISPLAY
--commands here--
<EOT>
```

You can substitute $DISPLAY with the output from:
```
env | grep DISPLAY
```
(i am not sure if it would make any difference)
EDIT: It does make difference! $DISPLAY doesn't work for me, i need to write ```
export DISPLAY=:0.0
```
(You might have something different from :0.0)

---

### Post by fredscripts on 2007-08-31
I still don't get the "classical" way working :( and I don't understand the DISPLAY stuff. I'm using the pipe way to get things done(```
echo "DISPLAY=$DISPLAY konqueror ~/LinuxDoc/KubuntuDesktopGuide.pdf" | at now
```), but I'm curious about the DISPLAY thing, could anyone explain me why it is used in order to get "at" to work?


Thank you very much!

---

### Post by fredscripts on 2007-08-31
Wow! I've found an interesting thing about the at command:

```
fredscripts@laptop:~$ sudo at now
Password:
warning: commands will be executed using /bin/sh
at> shutdown -r now<EOT>
job 38 at Fri Aug 31 13:39:00 2007
fredscripts@laptop:~$

```

This works!!!! , I mean the system gets rebooted if I run that code. But the bad news are that only the "shutdown -r now" command works, If I do, for example:

```
fredscripts@laptop:~$ sudo at now
Password:
warning: commands will be executed using /bin/sh
at> firefox<EOT>
job 38 at Fri Aug 31 13:44:00 2007
fredscripts@laptop:~$
```

Firefox (or konqueror or any other desktop program I've tried) doesn't get launched.

Kind of funny the behavior of the at command!!:mad: but maybe with the sudo stuff I get on the right way of solving the "at" command problem. If only someone could help me with it.


Thank you very much for your help!

---

### Post by spupy on 2007-08-31
Ok, im not really sure about the things i am gonna say, but here goes:
This command
```
export DISPLAY=:0.0
```
makes a shell (runtime? don't know how its called) variable named DISPLAY, which points the display you are using; display meaning here the physical display of your computer. This makes more sense if you got a dual-monitor setup, this variable tells which display to use for whatever it is set. ( im not really really sure about this thou).
Write this in your terminal
```
env | grep DISPLAY
```
You **must** use the output of this command when you "export DISPLAY". 
```
export DISPLAY=$DISPLAY
``` doesn't work, at least for me.
For me the output is
```
DISPLAY=:0.0
```
Means i use display :0.0. So when i need the DISPLAY variable i must type
```
export DISPLAY=:0.0
```
I don't know  if this variable is set by default. 

Ok, that was about setting the variable; now lets explain why you actually need it.

Now for some reason im not aware of, scripts in "at" need this variable explicitly set for commands like "gedit" or "firefox" to work. Because these applications are graphical, they need a display to pop up at. This is what DISPLAY variable is for. It tells on which display the programs should "appear".
The shutdown command you used with sudo is not graphical, so it worked without DISPLAY set, because it doesn't need one. Firefox on the other hand needed one, but couldn't find it.

The rule of thumb, if you can "see" the command you want to use in "at"  (that means if its graphical - has windows, etc.), you need to set the DISPLAY variable.

---

