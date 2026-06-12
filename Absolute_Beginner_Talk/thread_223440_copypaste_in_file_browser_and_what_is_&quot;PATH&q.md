---
title: "copy/paste in file browser and what is &quot;PATH&quot;"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by secallen on 2006-07-26
Hi,

I'm trying to install RealPlayer as a plugin in Firefox. I've downloaded the application and it works as free-standing, but does not embed in Firefox. I am trying to follow these instructions from Mozilla:

   1. Install RealPlayer 10.
   2. Copy nphelix.so to your Mozilla plugins directory and nphelix.xpt to your Mozilla components directory.
   3. Make sure a symbolic link to the realplay script is in your PATH.

My questions are:

1) How do you paste a file into another folder once you've copied it in the file browser? 

2) What is my "PATH", what is the "realplay script" and how do I make a "symbolic link" to it??

Thanks for any help!! :D

---

### Post by Third Thoughts on 2006-07-26
> **secallen said:**
> Hi,

I'm trying to install RealPlayer as a plugin in Firefox. I've downloaded the application and it works as free-standing, but does not embed in Firefox. I am trying to follow these instructions from Mozilla:

   1. Install RealPlayer 10.
   2. Copy nphelix.so to your Mozilla plugins directory and nphelix.xpt to your Mozilla components directory.
   3. Make sure a symbolic link to the realplay script is in your PATH.

My questions are:

1) How do you paste a file into another folder once you've copied it in the file browser? 

Either hit control + v or right click and select paste

> 
2) What is my "PATH", what is the "realplay script" and how do I make a "symbolic link" to it??

Thanks for any help!! :D

Your PATH is the set of folders in which bash (the terminal) looks for files to execute. So if you have an executable file called foo and foo is not in your PATH and you type 
```
foo
```
At the command line, you'll get an error message. To figure out what folders are in your path type 
```
echo $PATH
``` 
As for the realplayer script stuff, when you installed Realplayer I'm guessing it made a folder somewhere? In that folder should be an executable file. That file is the realplay script. To create a symbolic link you use the ln command like so
```

ln -s <file you are linking to> <name of the new file that will be the link>

```
So to create the necessary symbolic link you should do something like
```

ln -s <name of realplayer file> /usr/local/bin/<name of realplayer file>

```

~Andrew S.

---

### Post by secallen on 2006-07-26
Hi,

Thanks for your reply.

When I try right-clicking to paste, the paste command is greyed out. Also, ctrl-v doesn't have any effect. Do I need to enable pasting or something??

Thanks

---

### Post by registering on 2006-07-26
It's sounds like the system isn't convinced you copied it, so it can't find anything worth pasting. Can you highlight the file, right-click and hit "copy"? If so, right-click again and see if "paste" works. Also, ctrl+c will let you copy via the keyboard, followed by ctrl+v to paste whatever was copied. Hope this helps.

---

### Post by secallen on 2006-07-26
Hi,

WHen I right-click copy or do ctrl-c, I get a message in the footbar saying "<filename> will be copied if you select the Paste command". Trouble is, there is no obvious paste command!

Any ideas?

---

### Post by PingunZ on 2006-07-26
Here's what you need to do
install automatix to take care of the realplayer
then for ctrl+v goto 
system -> preferences -> keyboard and select the keyboard variant you have

---

### Post by annda on 2006-07-26
aha, the file permissions problem again. sorry, i can't point you to a useful thread, but try searching for 'permission' or 'rights' later.

for now, make sure you run the file manager as a superuser, which will let you not only read files but also write in directories that you are not the owner of. in order to do that, type

```
gksudo nautilus
```

type your password on prompt and there you go! paste wherever you want.

you may also find this helpful:
[https://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html](https://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html)

---

