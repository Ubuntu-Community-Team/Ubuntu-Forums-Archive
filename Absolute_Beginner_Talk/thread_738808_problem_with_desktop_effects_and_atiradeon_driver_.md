---
title: "problem with desktop effects and ati/radeon driver resolves itself temporarily"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by daberger on 2008-03-29
ive had a huge problem trying to enable desktop effects and after 62 posts have come to a temporary solution
running ```
SKIP_CHECKS=yes compiz

```
resolves the issue temporarily allowing me to use those bootiful effects. when i reboot i lose this and im also having trouble with themes and i think it may b correlated. i seek expert help. plllllz

i am running hardy in case f that has anything to do with it

---

### Post by hhhhhx on 2008-03-29
messy fix:
```
system>adminastration>sessions>
    make a new launcher with that command to run on startup
```

---

### Post by daberger on 2008-03-29
ty. but im still open to a permanent fix

---

### Post by Mehashi on 2008-03-29
Ive been having these problems (many of them!) with my ati drivers too.

This 'temporary fix', would that mean that I could enable desktop effects even if I cant use the restricted drivers? 
And where do I enter that command, in the console or xorg.conf? 

Any help appreciated - it would be nice to see how my computer handles the effects but I just cant get around the drivers!
^_^

---

### Post by daberger on 2008-03-29
mehasi u enter this command and if it works u can have it do that on start up through System>Administration>Sessions (although im not sure how it is in gutsy) and then adding a new start up thingy. this will b the terminal with the command SKIP_CHECKS=yes compiz.

for more detailed information on permanent fixes that may work for u refer to this thread
[http://ubuntuforums.org/showthread.php?t=738321](http://ubuntuforums.org/showthread.php?t=738321)

---

### Post by misterhead on 2008-03-29
mkdir -p ~/.config/compiz && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

This will create a file in your home folder which makes sure that Compiz will run without without having to type "SKIP_CHECKS" manualy. That's how mine is running.

---

### Post by forrestcupp on 2008-03-29
> **misterhead said:**
> mkdir -p ~/.config/compiz && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

This will create a file in your home folder which makes sure that Compiz will run without without having to type "SKIP_CHECKS" manualy. That's how mine is running.

That's what I was going to suggest, only I put mine in /etc/xdg/compiz with the file name compiz-manager.

Just copy the command misterhead posted, and it will work every time it starts up.  That makes a kind of configuration file that tells compiz to skip the checks every time it starts.

---

### Post by Mehashi on 2008-03-31
Cheers boys!
Have been having issues with my windows hard-drive (haha like im suprised!) that have been causing terminal errors in the system when using steam, so i've been distracted for a few days.
Working on my ubuntu tonight and i'll try this straight away! Thanks for the repsonses!
^_^

---

