---
title: "how to install js2mouse.tar.gz"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by jryprt on 2007-09-06
Hi: I am trying to install js2mouse from here [http://cedric.vincent.perso.free.fr/Projets/index.html](http://cedric.vincent.perso.free.fr/Projets/index.html)
I have tried the guide on the website i get
jerry@ip68-99-21-16:~$ tar -xvzf js2mouse-040208.tar.gz
tar: js2mouse-040208.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
jerry@ip68-99-21-16:~$ 
jerry@ip68-99-21-16:~$ 
can someone give me step by step on how to install this I am very new to this .
How do you post a screenshot ?
Thanks Jerry

---

### Post by diatribe on 2007-09-06
you are not in the right directory, switch to the directory you downloaded the file to and try again

---

### Post by Perfect Storm on 2007-09-06
```
cd ~/Desktop
tar -xvzf js2mouse-040208.tar.gz
```

If it's source code you need to compile, you need the right tool as well. Usually:

```
sudo aptitude install build-essential
```

---

### Post by jryprt on 2007-09-06
[QUOTE=diatribe;3321657]you are not in the right directory, switch to the directory you downloaded the file to and try again[/QUOTE

Can you tell me with directory & how to do  it
I am new to terminals & linux 
Thanks Jerry

---

### Post by CapnGimp on 2007-09-07
we have him online in our forums
 [http://sci.rutgers.edu/forum/showthread.php?p=714478&posted=1](http://sci.rutgers.edu/forum/showthread.php?p=714478&posted=1)
and he has it installed...  NOW we have to modify the Xorg.conf file and maybe get something put into the kernel so it works upon boot.
 If there is someone who can help us, come on over there and post, he has very minimal use of his hands, therefore the NEED to use a joystick to input mouse movements
 all help is greatly appreciated!!
4pm eastern on Friday

there are example files in the DOCUMENTS folder from the tarball, I'm just not sure how to do this and not screw something up

---

