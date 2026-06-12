---
title: "[SOLVED] Folding at Home operational?"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-11-25
From:

Folding 0.5.2 “User Friendly” Release  [http://ubuntu-tutorials.com/](http://ubuntu-tutorials.com/)

I installed Stanford Univ.'s Folding-at-Home project.

The install reported successful install.

Now that I have it, how can I tell if it's doing something? I know this sounds dumb, but I have no way to know it runs when I power up the computer. I don't see anything in System Monitor.

---

### Post by Flying caveman on 2007-11-25
I'm not familiar with that version or how you installed it.  I can tell you that you will see your CPU usage go way up and you will see it as a process in system monitor.

You may want to read this. [http://www.stanford.edu/group/pandegroup/folding/console-userguide.html](http://www.stanford.edu/group/pandegroup/folding/console-userguide.html)

from whatever directory you installed it to you need to run it.

```
./FAH502-Linux.exe 
```
 but the first time you should run it with the -config flag like so ```
./FAH502-Linux.exe -config
```

* your version might be different

EDIT: is Directory a windows thing or is it just a folder? ..anyway...

---

### Post by Mark_in_Hollywood on 2007-11-25
Ah, thanks, if you would look at the link I included, you will see that it has an installer for Ubuntu Gutsy. I ran it. It installed sucessfully according to the installer. I just don't see anything labeled FAH or Folding in System Monitor. Shouldn't something be there?

---

### Post by glotz on 2007-11-25
There's something in the link in my signature. Welcome to folding for Ubuntu! :)

---

### Post by Mark_in_Hollywood on 2007-11-25
> **glotz said:**
> There's something in the link in my signature. Welcome to folding for Ubuntu! :)

I had a look at the Ubuntu Wiki via your:

__________________
A distributed computing effort to understand protein folding - [https://help.ubuntu.com/community/FoldingAtHome](https://help.ubuntu.com/community/FoldingAtHome) 

"The client writes a log file in WD/FAHlog.txt. For fah_install, this is in /opt/foldingathome/#/FAHlog.txt or $HOME/opt/foldingathome/#/FAHlog.txt, where '#' is a digit from 1 to 9, but probably only 1 will exist unless you have a multiprocessor system. If you use finstall, it is in $HOME/foldingathome/CPU#."

mark@Lexington:~$ locate FAHlog.txt
/var/folding/foldingathome/CPU1/FAHlog.txt
mark@Lexington:~$ gedit /var/folding/foldingathome/CPU1/FAHlog.txt
 
So I had a look at it and there does seem to be work being done. 
[B]
Thank you all.[/B]

---

