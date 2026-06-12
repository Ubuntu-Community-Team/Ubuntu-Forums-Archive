---
title: "gparted live cd problems"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by broekskw on 2008-02-03
ok followed install guides from other site , burned iso image to cd-r and am running on a new 40gb win xp system to partition about 20gb to get ready for ubuntu, but everytime i run from gparted live cd i can not get the fluxbox menu program to load up to make my adjustments, there is not program on this cd that said fluxbox, after the cd loads i have the following programs that i can type in and then hit enter to load them 
vim, partimage, testdisk, mc, mtfs-3

also i have an error message that i think stops gparted program from running

"x.org:you need a graphical environment to start gparted, the graphical environment should have been done automatically unfortunately it did not, since you are back to the bash

so please run "forcevideo script, & you will be asked for video driver & resolution

so how or what is the correct command to run forcevideo script??

thanks

---

### Post by freebeer on 2008-02-03
I think you just need to type "Forcevideo"  (I've never used the gparted Live CD).  Another thread noted that the script has a capital "F" in the name... remember that the Linux file system is case sensitive, so "forcevideo" and "Forcevideo" are different files/commands as far as the file system is concerned.

---

### Post by broekskw on 2008-02-03
thanks freebeer, yes case sensitive is correct also found that out in this post

[http://ubuntuforums.org/showthread.php?t=654352&highlight=forcevideo+script+command&page=2](http://ubuntuforums.org/showthread.php?t=654352&highlight=forcevideo+script+command&page=2)

just that simple:lolflag:

---

### Post by freebeer on 2008-02-03
you're welcome.  Glad it worked out. [IMG]http://www.freebeer.is-a-geek.org/graphics/thumbsup.gif[/IMG]

If that solved your problem, you should edit your title and mark it as "solved"... that way folks who are trying to help know that your issue is solved, so they can move on to another subject.  Just a little courtesy thing we do here to keep things flowing.  ;)

---

