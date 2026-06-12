---
title: "&quot;Sufficiently new version of plib not found&quot; - say what? :)"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by emarkay on 2007-01-17
Installing fgrun program (for FlightGear) and got it to finally "./configure"  (Took a while to figure out the nonsense about the missing C compiler...).

Well it goes through the configure process and stops at:

"checking for PLIB - version >=1.8.0 ...not present
configure: error: Sufficiently new version of plib not found"

and then it goes back to the command line.

Anyone have some info and a solution?

Thanks.

---

### Post by riven0 on 2007-01-17
Have you tried installing plib yet?:

> sudo apt-get install plib1.8.4c2 plib1.8.4-dev plib1.8.4-pic

---

### Post by emarkay on 2007-01-18
Strange that I get this:  Ant ideas?


Reading package lists... Done
Building dependency tree... Done
plib1.8.4c2 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  plib1.8.4-dev: Conflicts: plib-dev
                 Conflicts: plib1.8.4-pic but 1.8.4-3ubuntu1 is to be installed
  plib1.8.4-pic: Conflicts: plib-dev
                 Conflicts: plib1.8.4-dev but 1.8.4-3ubuntu1 is to be installed
E: Broken packages

---

### Post by bdk on 2007-01-27
emarkay, I had the same initial problem... I ran:

```

sudo aptitude install plib1.8.4-dev

```

and plib-dev installed fine. You will also need to install simgear-dev:

```

sudo aptitude install simgear-dev

```

I'm getting lots of errors during the make process that look to be because I don't have a joystick installed right now...

---

