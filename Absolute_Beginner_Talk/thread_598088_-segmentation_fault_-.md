---
title: "-segmentation fault -"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by sleep furious idea on 2007-10-31
Hi all,

I'm a beginner who recently upgraded to gutsy from feisty and am having problems with segmentation faults.  
Here is an example:

moods@moods-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Segmentation fault (core dumped)
moods@moods-laptop:~$ synaptic
Segmentation fault (core dumped)
moods@moods-laptop:~$ 


What is this problem? 
How  can it be solved?


Thanks,
sfi

(regretting upgrading to gutsy now)

---

### Post by Partyboi2 on 2007-10-31
what does it say in /var/crash?

---

### Post by macogw on 2007-10-31
"Segmentation fault" is a general crash in C.  C is, unfortunately, not very descriptive of its crashes.  

Hmm it segfaulted on apt-get too, so the problem isn't with synaptic, it's apt.  

Can you do
```
ulimit -c unlimited
synaptic
```
The first line will make it so that it can dump core, and it will dump all of the memory trace when synaptic segfaults into a file called core (Ubuntu's default is to not dump core, since most normal users won't know how to use a core file to figure out what's wrong) in the directory from which you are running it (probably your home directory).  Please attach that core file to this thread, and I (or someone else if they beat me back to here) can put it through gdb and see where it died.   It should hopefully show what it was trying to do when it died, so we can figure out what is broken underneath.  

If you have gdb installed on your system (I rather doubt it, because if you did, it'd mean you're probably a programmer, and if you're a programmer, you'd likely know what a core dump is), you can do "gdb synaptic" and watch what calls it makes as it runs.  If you can download gdb from packages.ubuntu.com and use GDebi to install it (assuming GDebi works...if it doesn't, try "sudo dpkg -i <package" in the directory where you downloaded it), then run "gdb synaptic" and attach the output, that could also be useful.

---

### Post by sleep furious idea on 2007-10-31
> **Partyboi2 said:**
> what does it say in /var/crash?


Here are some:

/var/crash/_usr_sbin_synaptic.0.crash

/var/crash/_usr_sbin_synaptic.1000.crash

/var/crash/_usr_share_apport_apport-gtk.1000.crash


Not sure if this is what you mean.  Ironically it seems to crash when sending the crash report also.

---

### Post by macogw on 2007-10-31
> **sleep furious idea said:**
> Here are some:

/var/crash/_usr_sbin_synaptic.0.crash

/var/crash/_usr_sbin_synaptic.1000.crash

/var/crash/_usr_share_apport_apport-gtk.1000.crash


Not sure if this is what you mean.  Ironically it seems to crash when sending the crash report also.

But what does it say inside those files?

---

### Post by sleep furious idea on 2007-10-31
[/QUOTE] Hmm it segfaulted on apt-get too, so the problem isn't with synaptic, it's apt.  

Can you do
```
ulimit -c unlimited
synaptic
```
The first line will make it so that it can dump core, and it will dump all of the memory trace when synaptic segfaults into a file called core (Ubuntu's default is to not dump core, since most normal users won't know how to use a core file to figure out what's wrong) in the directory from which you are running it (probably your home directory).  Please attach that core file to this thread, and I (or someone else if they beat me back to here) can put it through gdb and see where it died.   It should hopefully show what it was trying to do when it died, so we can figure out what is broken underneath.  

If you have gdb installed on your system (I rather doubt it, because if you did, it'd mean you're probably a programmer, and if you're a programmer, you'd likely know what a core dump is), you can do "gdb synaptic" and watch what calls it makes as it runs.  If you can download gdb from packages.ubuntu.com and use GDebi to install it (assuming GDebi works...if it doesn't, try "sudo dpkg -i <package" in the directory where you downloaded it), then run "gdb synaptic" and attach the output, that could also be useful.[/QUOTE]

Thanks for your helpful reply.  

I did the first part as you said and I tried attaching said 'core' file but I couldn;t on account of this:

Upload errors

core:
invalid file

I will try to download gdb and follow your second step (but i'm sure i will have no clue what the problem is when i see it).  

sleep furiously

---

### Post by macogw on 2007-10-31
right click on core and choose "create archive" and make it a zip, then upload the zip.  it just doesnt like the lack of file extension.

---

### Post by sleep furious idea on 2007-10-31
...Thanks, I'll post the 'core file' and the crash file in the next post...

---

### Post by sleep furious idea on 2007-10-31
> **sleep furious idea said:**
> ...Thanks, I'll post the 'core file' and the crash file in the next post...

...i would have, but the files are about 30kb too big still to attach here.

What can I do about that?


(I can feel the learning curve stretching on the axis as i type.)

---

### Post by macogw on 2007-10-31
well that's annoying... can you paste the contents of the crash file in a pastebin (like [http://pastebin.ca](http://pastebin.ca)) and link to it?  If you want to just email me the core at macoafi AT gmail DOT com, i'll look at it with gdb.

Oh, I lied, it's not *just* C that gives very unhelpful segfaults with no explanation.  C++ does it too, and it does it more.
Knock knock
Who's there
C plus pl--segfault!

---

### Post by sleep furious idea on 2007-11-04
It is a mystery to me but the problem seemed to fix itself.  

I burned a gutsy cd on another computer and did a check of the cd and when I rebooted the segmentation faults no longer happen.

Have no idea why but everything seems fine now.

Thanks for looking in to it Mac.

---

