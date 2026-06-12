---
title: "Uninstalling software??"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by broncbuster on 2007-01-29
I recently installed VNC from an .rpm package.  I used alien to install it, but i can't figure out how to uninstall it so i can reinstall a different version.  How is this done?  I tried to install over the original and i got this response:

administrator@LinuxBox:~/Desktop$ sudo alien -i vnc.rpm
Warning: Skipping conversion of scripts in package vnc: postinst
Warning: Use the --scripts parameter to include the scripts.
dpkg: regarding vnc_4.1.2-2_i386.deb containing vnc:
 xvncviewer conflicts with vnc
  vnc (version 4.1.2-2) is to be installed.
dpkg: error processing vnc_4.1.2-2_i386.deb (--install):
 conflicting packages - not installing vnc
Errors were encountered while processing:
 vnc_4.1.2-2_i386.deb
administrator@LinuxBox:~/Desktop$ 

What is this telling me?  I've been told that i need to resolve some dependencies, but i don't know how or what those dependencies are.  I just want to uninstall VNC and then reinstall it from the terminal.

Any help is greatly appreciated.

---

### Post by NewOldTimer on 2007-01-29
Hey broncbuster, maybe this will help [http://www.ubuntuforums.org/archive/index.php/t-224829.html](http://www.ubuntuforums.org/archive/index.php/t-224829.html)

---

### Post by meng on 2007-01-29
sudo dpkg -r vnc

but I would advise you to look for an alternative program - the error message says that vnc conflicts with xvncviewer. In any case, installing from aliened rpm is a poor choice generally.

---

### Post by broncbuster on 2007-01-29
Thanks y'all.  This is all so new and cool to me.  I have a lot to learn and i think that's exciting.  I thought I knew a lot about computers until now.  Now i'm realizing that there's a whole world out there, heretofore undiscovered by me.

---

