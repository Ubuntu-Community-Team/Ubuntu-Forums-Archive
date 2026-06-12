---
title: "How do I find the System information?"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by The Iron Curtain on 2006-12-08
Hello, new Linux user..

I looked around but I couldn't find an answer to my following question:

How do I find out information on my cpu (like the type and speed) as well as memory and graphics card. I have a laptop, so it's much harder to take apart and look for myself :p 

Thank you all!

---

### Post by anti_microsoft on 2006-12-08
I think you can do #cat /proc/cpuid off the top of my head not in linux right now.

---

### Post by amo-ej1 on 2006-12-08
cat /proc/cpuinfo

gives you all the information on the cpu's

cat /proc/meminfo 

gives you more information than your mind can ever understand on your memory (free -m is a bit more readable)

lspci 

gives you information on all PCI cards.

There are probably some graphical tools to do the same also ;)

---

### Post by The Iron Curtain on 2006-12-08
Wow! thank you very much. I don't mind using the CLI :)

---

### Post by _simon_ on 2006-12-08
Or if you want a gui then install hardinfo from Add/Remove in your Applications menu or via Synaptic.

See attached screenshot.

EDIT: YOU MIGHT HAVE PROBLEMS WITH IT SEGFAULTING - PLEASE SEE MY POST FURTHER DOWN IN THE THREAD.

---

### Post by a.v.l on 2006-12-08
> **_simon_ said:**
> Or if you want a gui then install hardinfo from Add/Remove in your Applications menu or via Synaptic.

See attached screenshot.

Just tried "hardinfo" and it keeps crashing when selecting certain items such as pci devices, usb devices etc. This doesn't happen on every selection, just the ones lower down the list of items to check.  Any ideas how to stop this happening?

---

### Post by L Campbell on 2006-12-08
> **The Iron Curtain said:**
> Wow! thank you very much. I don't mind using the CLI :)

Another command that will tell you a lot about your computer is ' lshw ', which they recommend to run as ' sudo '.

---

### Post by _simon_ on 2006-12-08
> **a.v.l said:**
> Just tried "hardinfo" and it keeps crashing when selecting certain items such as pci devices, usb devices etc. This doesn't happen on every selection, just the ones lower down the list of items to check.  Any ideas how to stop this happening?

hmm yeah it's doing that for me.

You could download version 0.4.2RC1 which does seem to work without segfaulting.

[Download](http://prdownload.berlios.de/hardinfo/hardinfo-0.4.2RC1.tar.bz2)

Extract it somewhere.

Then in terminal:

```

cd /location/hardinfo-0.4.2RC1

```

Obviously the location depends on where you extracted it.

```

./configure

```

```

make

```

```

sudo make install

```

All done. You should find it in Applications -> System Tools -> System Profiler and Benchmark

---

### Post by Sef on 2006-12-08
> Then in terminal:

Code:

cd /location/hardinfo-0.4.2RC1

Obviously the location depends on where you extracted it.

Code:

./configure

Code:

make

Code:

sudo make install



Before you install that, install build-essential.

```
sudo aptitude update
```

```
sudo aptitude install build-essential
```

If you don't, then you won't be able to compile.

---

### Post by _simon_ on 2006-12-08
I don't have build-essential installed yet I was able to compile :confused:

---

### Post by a.v.l on 2006-12-08
> **_simon_ said:**
> hmm yeah it's doing that for me.

You could download version 0.4.2RC1 which does seem to work without segfaulting.

[Download](http://developer.berlios.de/project/showfiles.php?group_id=5897)

Extract it somewhere.

Then in terminal:

```

cd /location/hardinfo-0.4.2RC1

```

Obviously the location depends on where you extracted it.
0.4.2RC1
```

./configure

```

```

make

```

```

sudo make install

```

All done. You should find it in Applications -> System Tools -> System Profiler and Benchmark


I've downloaded the 0.4.2RC1 software how do I extract it, as there are no options to do this that I can see?

---

### Post by _simon_ on 2006-12-08
All you need to do is right click on it and choose "extract here".

Failing that, Applications -> Accessories -> Archive Manager

That's assuming you didn't download the autopackage one which I don't know what you do with!

Here's the link for the tar.bz2: [http://prdownload.berlios.de/hardinfo/hardinfo-0.4.2RC1.tar.bz2](http://prdownload.berlios.de/hardinfo/hardinfo-0.4.2RC1.tar.bz2)

---

### Post by a.v.l on 2006-12-08
> **_simon_ said:**
> All you need to do is right click on it and choose "extract here".

Failing that, Applications -> Accessories -> Archive Manager

That's assuming you didn't download the autopackage one which I don't know what you do with!

Here's the link for the tar.bz2: [http://prdownload.berlios.de/hardinfo/hardinfo-0.4.2RC1.tar.bz2](http://prdownload.berlios.de/hardinfo/hardinfo-0.4.2RC1.tar.bz2)

Ah, I did download the autopackage one.  I'll try again. Thanks

---

### Post by a.v.l on 2006-12-08
> **_simon_ said:**
> hmm yeah it's doing that for me.

You could download version 0.4.2RC1 which does seem to work without segfaulting.

[Download](http://prdownload.berlios.de/hardinfo/hardinfo-0.4.2RC1.tar.bz2)

Extract it somewhere.

Then in terminal:

```

cd /location/hardinfo-0.4.2RC1

```

Obviously the location depends on where you extracted it.

```

./configure

```

```

make

```

```

sudo make install

```

All done. You should find it in Applications -> System Tools -> System Profiler and Benchmark

I used the non autopackage and followed the above information but terminal gave me this message after my last input. 
" No rule to make target "install". Stop:-k

---

### Post by _simon_ on 2006-12-08
When you used the make command did that give any errors at all?

when you are doing sudo make install, are you still in the hardinfo-0.4.2RC1 directory?

---

### Post by a.v.l on 2006-12-08
> **_simon_ said:**
> When you used the make command did that give any errors at all?

when you are doing sudo make install, are you still in the hardinfo-0.4.2RC1 directory?


At the ./configure point I get this. I've tried but I cannot install  aptitude install libgtk2.0-dev in root as suggested below.

:~/hardinfo-0.4.2RC1$ ./configure
ToscoConf (version 0.04) for hardinfo version 0.4.2RC1
Determining system architecture.
Compiling hardinfo for Linux i686 (ARCH_i386).

Checking for lspci... /bin/lspci
Checking for GTK version >= 2.6.0... not found.

You need the GTK libraries, including the development stuff.
If you're using Debian, running the command as root:

        aptitude install libgtk2.0-dev

Will do the trick.
:~/hardinfo-0.4.2RC1$

---

### Post by _simon_ on 2006-12-08
You should be able to install libgtk2.0-dev via synaptic.

---

### Post by OldDogNewTricks on 2006-12-08
> **_simon_ said:**
> Or if you want a gui then install hardinfo from Add/Remove in your Applications menu or via Synaptic.

See attached screenshot.

EDIT: YOU MIGHT HAVE PROBLEMS WITH IT SEGFAULTING - PLEASE SEE MY POST FURTHER DOWN IN THE THREAD.

I had the segfault problem when trying to look at individual statistics. But if you use the "Generate Report" option it seems to get all the information without crashing.  And you have a nice printable record too.

---

### Post by louieb on 2006-12-08
When I ran the ./configure command. it gave me the message I need to:
```
sudo aptitude install libgtk2.0-dev
```Which I did.
It added some stuff and the [COLOR=Red]command also removed the kUbuntu-desktop[/COLOR] from the PC.  
No big loss I mostly use Gnome anyway.   But I would like to know why?
BTW System Profiler and Benchmark did install. I ran it and it works. (P2 400  PC).

---

### Post by _simon_ on 2006-12-09
I have absolutely no idea as to why it removed kubuntu-desktop.

When installing anything, always double check exactly what it's telling you so that you don't get any nasty surprises once installation is completed. :-k

---

### Post by louieb on 2006-12-09
I believe someone around here has "[COLOR=Teal]Experience is what you get after you need it[/COLOR]" in their signature.:twisted:

---

