---
title: "adding to the directory??"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by superjdf on 2007-08-28
How do I add new files, items etc. to my directory???
I am running dapper, and I am trying to add win32 under /usr/lib so I can add some plug-ins to kaffeine???

If I do so under system files it says permisiion denied?? Thats the other thing that annoys me is the whole permissions thing.

So how would one do these things???:confused:

---

### Post by jfinkels on 2007-08-28
> **superjdf said:**
> How do I add new files, items etc. to my directory???
I am running dapper, and I am trying to add win32 under /usr/lib so I can add some plug-ins to kaffeine???

If I do so under system files it says permisiion denied?? Thats the other thing that annoys me is the whole permissions thing.

So how would one do these things???:confused:

Take a look at the link in my signature "Root & Sudo".

To make a directory in a directory in which you don't have rights, type the following in the terminal:```
sudo mkdir /path/to/dir
```
where /path/to/dir is the directory you wish to create. Type your password when prompted.

---

### Post by superjdf on 2007-08-28
How do I add my plugins to it now???

---

### Post by superjdf on 2007-08-28
Ok I made a mistake I created the file now I want to add to it how do I do that???

---

### Post by jfinkels on 2007-08-28
> **superjdf said:**
> Ok I made a mistake I created the file now I want to add to it how do I do that???

I'm afraid we're going to need a little more information on what you are doing before we can help you...if you are following instructions on a website, can you post the link?

Explain exactly what you are trying to do, the steps you have taken already, and where you are having problems (giving us output from the terminal is helpful, if there is any).

---

### Post by superjdf on 2007-08-28
I just added the commands you told me and created the file!!
Now I am trying to add two item to that file but I do not know how I guess??
heres the link [http://ubuntuforums.org/showthread.php?t=535692](http://ubuntuforums.org/showthread.php?t=535692)

There you go I hope that clears it up!!

---

### Post by jfinkels on 2007-08-29
> **superjdf said:**
> I just added the commands you told me and created the file!!
Now I am trying to add two item to that file but I do not know how I guess??
heres the link [http://ubuntuforums.org/showthread.php?t=535692](http://ubuntuforums.org/showthread.php?t=535692)

There you go I hope that clears it up!!

First thing you should do is read this: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Second, to run a program (in this case, 'cp' to copy the files), type the following in the terminal:```
sudo cp /path/to/source /path/to/destination
```
where "/path/to/source" is the path to the file that you want to copy, and "/path/to/destination" is the location to which you want to copy the file.

---

