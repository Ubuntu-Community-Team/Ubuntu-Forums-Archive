---
title: "Frostwire Wont Start"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by NewRubberSoul on 2006-09-30
Hi everyone. 

Just reading the forums, I figured that most people prefered to run Frostwire rather than Limewire.  I went to the Frostwire website and downloaded the program.  When I opened it, the system installed it and it is in my >applications >internet menu.  

The only problem is that when I click on the icon in the menu, Frostwire does absolutely nothing.  It doesn't bring up a splash page or open the program or anything.  

Does anyone know what might be wrong, or might be able to suggest a similar P2P with a limewire-type interface and good selection of mp3s?

Thanks! :cool:

---

### Post by IusedTObeSOMEONEelse on 2006-09-30
Have you got java enabled? I went through the same experience. Also when I upgraded from dapper to edgy I had to change dash to bash. Can get to that later.

---

### Post by bulldog on 2006-09-30
Did you install java too?

It's necessary for frostwire.

Do a search in synaptic at jre and you should find it.

---

### Post by easyease on 2006-09-30
once you have downloaded java 1.5 you may have to set it as the default java environment, if you have older java versions that is.

 sudo update-alternatives --config java
then select the number corresponding to the java 1.5, to make it default.

---

### Post by NewRubberSoul on 2006-09-30
I did a synaptic search for "JRE" as bulldog suggested and I have these packages installed:

[LIST]
[*]sun-java5-bin    -  Sun Java(TM) Runtime Environment (JRE) 5.0
[*]sun-java5-jre
[*]sun-java5-plugin  -  The Java(TM) Plug-in, Java SE 5.0
[/LIST]

Should This be enough?  :confused:

---

### Post by PriceChild on 2006-09-30
yes, but then do
```

 sudo update-alternatives --config java
``` and use sun 1.5.0 as default.

if this still doesn't work, start frostwire from a terminal (just type frostwire then enter) and paste the output!

---

### Post by NewRubberSoul on 2006-09-30
AWESOME :KS 

Thanks to all three of you for the help.  Easyease, I typed that command and then was given three options.  I typed the third, that corresponded to one you mentioned and Frostwire popped up with no problems.

Look, only five minutes and the problem is solved.  You folks always make me remember why I use Ubuntu!

---

### Post by easyease on 2006-09-30
no worries mate! had the same problem myself a while back and couldnt quite remember the magic words myself, so i looked back into my terminal history to find it, the way i see it by helping you im helping myself to try and make the command line sink into my brain.lol :-D

---

### Post by westsurf on 2006-12-03
I followed the above and stil cannot get my frostwire working.

My terminal looks like this after running frostwire:

westsurf@tux:~$  sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
          2    /usr/bin/gij-wrapper-4.1
 +        3    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 1
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.
westsurf@tux:~$ frostwire
runFrost.sh: 44: Syntax error: "(" unexpected (expecting "}")
westsurf@tux:~$ 


Any ideas. Thanks in advance.

---

### Post by RanDinCarolina on 2006-12-03
I think you've got the bash problem. look it up in the forums 'cause I can't remember where I got the fix. 
Basically, you'll need to make a change to the shell to make it work. Sorry, I can't remember where it was......

---

### Post by xpod on 2006-12-03
Had it myself.....Post 6 should help

[http://ubuntuforums.org/showthread.php?t=278688](http://ubuntuforums.org/showthread.php?t=278688)

---

### Post by westsurf on 2006-12-03
> **RanDinCarolina said:**
> I think you've got the bash problem. look it up in the forums 'cause I can't remember where I got the fix. 
Basically, you'll need to make a change to the shell to make it work. Sorry, I can't remember where it was......

See [http://ubuntuforums.org/showthread.php?t=300954](http://ubuntuforums.org/showthread.php?t=300954).

or as here:

If you follow the instructions in the guide, FrostWire won't start and will show the error:
Code:

runFrost.sh: 44: Syntax error: "(" unexpected (expecting "}")

There seems to be a problem with the init scripts, perhaps the text format; but dash doesn't like it so a quick fix is to edit /usr/bin/frostwire and use bash instead of sh to load runFrost.sh:
Code:

#!/bin/bash 
cd /usr/lib/frostwire 
bash runFrost.sh

Thanks for the directions:)

---

### Post by Frak on 2006-12-13
[http://ubuntuforums.org/showthread.php?t=315222&highlight=frostwire](http://ubuntuforums.org/showthread.php?t=315222&highlight=frostwire)

---

