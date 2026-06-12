---
title: "Where to store script files?"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Anders J on 2007-12-31
I have created an executable script file that starts a certain program (Eagle) with some parameters. I have found out how to make it executable and it works fine.

Now, to be able to start it without looking it up each time, there should be a common place for files like that where the OS is expecting scripts to be found, shouldn't it?

---

### Post by thenailedone on 2007-12-31
All scripts in the /etc/ folder automatically runs AFAIK...

---

### Post by Cypher on 2007-12-31
I usually create a "bin" directory in my home directory and add that my path in ".bash_profile" in the PATH statement. 

So you could add "export PATH=$PATH:~/bin" to the file and use the script from the command line. If you wanted to launch it within Gnome, then you would create a custom launcher and just point to the file in it's full path..

---

### Post by fiddledd on 2007-12-31
You can put it in home/user_name/bin and that will be found as it's in the $PATH environment variable. If bin doesn't exist just create it.

---

### Post by Cypher on 2007-12-31
> **thenailedone said:**
> All scripts in the /etc/ folder automatically runs AFAIK...
User scripts shouldn't be placed in /etc and /etc is for configuration files. If you wanted something to be available to ALL users, then "/usr/local/bin" is OK, but for a particular use "~/bin" is the most appropriate..

---

### Post by fiddledd on 2007-12-31
Okay that's 3 times I replied too late. I think I need to type much faster, but it's hard as I'm an old man :)

---

### Post by thenailedone on 2007-12-31
> **Cypher said:**
> User scripts shouldn't be placed in /etc and /etc is for configuration files. If you wanted something to be available to ALL users, then "/usr/local/bin" is OK, but for a particular use "~/bin" is the most appropriate..

...Thanks... (so... it would work but isn't advisable... sorry Anders J I almost led you astray...)

---

### Post by Cypher on 2007-12-31
> **thenailedone said:**
> ...Thanks... (so... it would work but isn't advisable... sorry Anders J I almost led you astray...)
Technically, it wouldn't work either. :) The directories that are part of the PATH are usually, /bin, /sbin(depends on distro), /usr/bin, /usr/sbin, /usr/local/bin and ~/bin. The files in /etc are referenced by various applications and services that run in a Linux machine. But putting executable scripts doesn't mean that you could use them without providing the full path.

---

### Post by Anders J on 2007-12-31
Sorry folks, but this is the beginner's forum.

I have made a /home/my_name/bin directory and plaed it there, but it is still nout found.

"...as it's in the $PATH environment variable. If bin doesn't exist just create it."

So whee is the $PATH variable then?

---

### Post by thenailedone on 2007-12-31
> **Cypher said:**
> Technically, it wouldn't work either. :) The directories that are part of the PATH are usually, /bin, /sbin(depends on distro), /usr/bin, /usr/sbin, /usr/local/bin and ~/bin. The files in /etc are referenced by various applications and services that run in a Linux machine. But putting executable scripts doesn't mean that you could use them without providing the full path.

...Doh!... :)  Open mouth-->Remove foot-->Close mouth... (I remember when I was playing around with Peanut Linux in 98-99 that I got the impression that /etc was almost like autoexec.bat of MS-DOS of old... I must have been mistaken... again I must apologies...)

---

### Post by Cypher on 2007-12-31
> **Anders J said:**
> Sorry folks, but this is the beginner's forum.

I have made a /home/my_name/bin directory and plaed it there, but it is still nout found.

"...as it's in the $PATH environment variable. If bin doesn't exist just create it."

So whee is the $PATH variable then?
The PATH variable is located in either your .bash_profile or .bashrc file. The "." before the filenames mean that they are hidden. If you are doing all of this from the command line, you can do the following
```

gedit ~/.bashrc
gedit ~/.bash_profile

```
This will open both the files in a text editor and you can search/modify the PATH variable in the appropriate file and save it. Once you've made the change, close the Terminal and re-open it to have the new PATH take effect before trying your command.

How are you trying to launch your script?

---

### Post by Anders J on 2007-12-31
PATH did not exist in ~/.bashrc at all.

~/.bash_profile did not exist.

If I navigate to the directory using f inst Nautilus, then I can double-click it and run it. All I want to achieve is to simply press Alt+F2 and type the script name, both in this case and for any future scripts.

Edit:

I browsed some more information, which led me to add this line to /home/my_name/.bashrc file:
```
export PATH=$PATH:/home/anders/bin:
```
And that solved the problem and I am yet again a tiny little bit more fluent in this art!

---

