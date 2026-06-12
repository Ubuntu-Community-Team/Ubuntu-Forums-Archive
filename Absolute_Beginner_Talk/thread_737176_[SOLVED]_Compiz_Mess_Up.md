---
title: "[SOLVED] Compiz Mess Up"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by cldx on 2008-03-27
[EDIT] just in case you came here looking for a solution for your compiz problem, i dunno how i fixed it, it happened by mistake, so dont bother reading all my crap. This thread might as well be deleted since its not helpful at all. Pretty please Mr. Admin ? 

Hey guys and gals :)

Im very frustrated that my first post in this awesome forum has to be about such a bitter subject.

Lets get to it, my Compiz just totally blew up today, i had some updates running from the Update Manager and ever since my Compiz doesnt start up anymore. I guess i dont have to mention that my Desktop was kinda irritated about that and went on strike xD

During update i got an Error message saying something like "blabla is trying to write gconf.xml ???...which is also in package compiz-gnome", but stupid as i am i didnt really pay much attention and just clicked it away (guess that wasnt so smart right..)

Ive been searching for help through the web and found this little thing 

[http://ubuntuforums.org/showthread.php?t=495549](http://ubuntuforums.org/showthread.php?t=495549)

but the given solutions didnt really help me, anybody else encountered such issues?

Some info on my Computer:

Samsung P35 Notebook with an ATI Mobility Radeon 9700, proprietary driver running

Heres the terminal output for compiz --replace

```

me@client:~$ compiz --replace
/usr/bin/compiz.real (core) - Error: no 'core' plugin with ABI version '20080314' loaded

/usr/bin/compiz.real (ccp) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'


```

after running compiz --replace my AWN starts up just fine, but no window decorations (Yes the plugin is activated in ccsm before you start asking)

Ive read several things about such issues but i didnt wanna take any steps before i heard what some of you think it might be about, what frustrates me the most is the fact that i just wanted to update my PC like a "good user", and the official update messed up if its something terribly easy excuse me for being such a Linux-Noob. Ill stroll for solutions now and maybe somebody in the boards has the ultimate tip for me. Thanks in advance.

---

### Post by LowSky on 2008-03-27
I would reinstall compiz from synaptic.

---

### Post by cldx on 2008-03-27
already did so, i searched for COMPIZ and completely removed all packages associated with it, i rebootet the comp and installed again, same problem...ill see for a list of the packages i edited...brb

---

### Post by cldx on 2008-03-27
i did it!! I have no clue how but i fixed it oO 

i tried uninstalling all compiz related stuff for 2 more times and it seems the second time (third time alltogether) i caught the error somehow.

Thanks to everyone who might have tried to figure out the problem. I appreciate

me so happy right now :)

---

