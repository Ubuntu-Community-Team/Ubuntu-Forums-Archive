---
title: "Newbie installation trouble"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Haruko147 on 2007-06-15
I found the forum post:

[http://ubuntuforums.org/showthread.php?t=185650](http://ubuntuforums.org/showthread.php?t=185650)

and I have both the bcm43xx-fwcutter-006 and bcmwl5.sys sitting on my desktop. I'm very new, so apparently you have to install the fwcutter first but I don't know how to do this. If I type in the command as shown on the forum post (apt-get) it says:

E: Impossible to open the file varlib/dpkg/lock - open (13 permission not granted)
E: Unable to lock the admin directory (var/lib/dpkg/), are you root?

as soon as I do this hopefully my wireless will work

---

### Post by overdrank on 2007-06-15
> **Haruko147 said:**
> I found the forum post:

[http://ubuntuforums.org/showthread.php?t=185650](http://ubuntuforums.org/showthread.php?t=185650)

and I have both the bcm43xx-fwcutter-006 and bcmwl5.sys sitting on my desktop. I'm very new, so apparently you have to install the fwcutter first but I don't know how to do this. If I type in the command as shown on the forum post (apt-get) it says:

E: Impossible to open the file varlib/dpkg/lock - open (13 permission not granted)
E: Unable to lock the admin directory (var/lib/dpkg/), are you root?

as soon as I do this hopefully my wireless will work

Hi did you use *sudo* at the beginning of the command?;)

---

### Post by Haruko147 on 2007-06-15
lol ><

ok, so that fixes a lot, but I tried it out and it said:

Reading packet list...done
building dependency tree
reading state information....done
E: impossible to find the packet bcm43xx-fwcutter

---

