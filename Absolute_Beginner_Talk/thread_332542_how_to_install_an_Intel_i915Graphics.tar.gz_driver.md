---
title: "how to install an Intel i915Graphics.tar.gz driver"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by davesmith on 2007-01-06
hello, i am gradually setting up my m/c for ubuntu but need a little basic help with installing an intel graphics tarball.

I have downloaded the linux i915 graphics driver to my desktop (i915Graphics.tar.gz). I want to install it using the terminal, and then set screen resolution to the maximim. Can anyone help?
Thanks

---

### Post by petermck on 2007-01-06
I would install the xserver-xorg-video-i810 package instead. This supports i915. You may then need to run dpkg --reconfigure xserver-xorg.

---

### Post by az on 2007-01-06
Enable the universe repository and install the package.  You don't need to use the tarball.  It's already in the repositories.

sudo apt-get install 915resolution

---

### Post by davesmith on 2007-01-06
Thanks, i will try it
however, how is it done in the terminal, do you know the commands?

---

### Post by lexrexus on 2007-01-17
> **azz said:**
> Enable the universe repository and install the package.  You don't need to use the tarball.  It's already in the repositories.

sudo apt-get install 915resolution

Hello.  Are the repositories online?  I don't as yet have a linux compatible modem -
If these repositories aren't online but on my sys., how do I access???

---

### Post by mikewhatever on 2007-01-17
This may help you [http://ubuntuforums.org/showthread.php?t=331296](http://ubuntuforums.org/showthread.php?t=331296)

---

