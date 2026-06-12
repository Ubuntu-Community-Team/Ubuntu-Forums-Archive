---
title: "swf-player"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by shayvasa on 2007-11-13
it wont let me install this in the synaptic pacage manager it show me an error saying swf-player:
 Depends: libgtk2.0-0 but it is not going to be installed
i i already tryed to install it manually but still nothing....what can i do i really need this???

---

### Post by shayvasa on 2007-11-13
come on someone plz i need help

---

### Post by zabien1970 on 2007-11-13
STOP Read top sticky

---

### Post by p_quarles on 2007-11-13
Don't run that command. Read the sticky note on the forums menu.

---

### Post by shayvasa on 2007-11-13
ok i read it but how can i install the program??

---

### Post by rudeboyskunk on 2007-11-13
First of all, go to System>Adminstration>Software Sources and make sure all of your repos are enabled.  After doing that, open a terminal and run these two commands:

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

Then try again.

---

### Post by shayvasa on 2007-11-13
what r the repos?

---

### Post by gsub on 2008-01-15
er.. sorry to flog a dead horse, but im having the same problem.

i restored my laptop to factory defaults (Feisty) and then upgraded distro to Gutsy. Now, when I try to install swf-player using apt-get, i get the error message below. Could someone please help?

Oh, and all repositories are enabled. I ran the update and dist-update commands.




"
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  swf-player: Depends: libgtk2.0-0 (>= 2.10.3) but it is not going to be installed
E: Broken packages
"

---

### Post by otrojake on 2008-02-04
I was running into this issue too.  What's happening is the swf-player package is looking for libgtk version 2.10.3 or greater.  

Someone more knowledgeable than me would have to point you towards how to update libgtk, though.  By the looks of things (considering I can't find an upgrade available in Synaptic) I'd say that only version 2.0-0 is officially supported by Ubuntu.

---

