---
title: "ugh x server thing pops up on all my computers!"
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by taseal on 2005-09-21
I made a thread about this yesterday but seems like nobody is willing to help or can help me...

this is the 3RD computer i'm installing this on (well trying) and all of them come up with a warning saying that my x server has a problem...

this time (amd64 desktop) it says 

fatal server error:
no screens found

wtf? how am i reading this then?

 ](*,)

---

### Post by Jussi Kukkonen on 2005-09-21
[QUOTE=taseal]
fatal server error:
no screens found
 [/QUOTE]

This is a really generic message, and will probably come up with any fatal X error...

without seeing */var/log/xorg.0.log* it's really difficult to say anything.

---

### Post by taseal on 2005-09-21
[QUOTE=Jussi Kukkonen]This is a really generic message, and will probably come up with any fatal X error...

without seeing */var/log/xorg.0.log* it's really difficult to say anything.[/QUOTE]
 where would that be if i were to go in from the c drive?

mind you this is an install from the live cd =/

I wanna check it out before I install the program

---

### Post by mtron on 2005-09-21
You can't preform a harddisk install from an hoary LiveCD, so what makes you think that you did so?

But, to target your particular problem:

First, Gnu/Linux does not use drive letters like  Windows. for basics about Linux please read [http://www.ubuntuforums.org/showthread.php?t=13042](http://www.ubuntuforums.org/showthread.php?t=13042) and see this page for basic shell options: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

then back on your Computer boot it up till the shell, cd to /var/log/ and open xorg.0.log with e.g. "sudo nano xorg.0.log"

additionaly you can try to reconfigure your xserver with "sudo dpkg-reconfigure xserver-xorg" but you will need some information about your computers hardware. 

But i really encourage you to browse the pages i posted!

---

