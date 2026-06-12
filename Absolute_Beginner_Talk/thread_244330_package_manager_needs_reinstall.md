---
title: "package manager needs reinstall"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by mlie on 2006-08-26
I tried to install jedit using .deb file (which is located at my Home folder). But there was a problem during installation, and the package manager now gives me an error message:
"The package jedit needs to be reinstalled but I can't find an archive for it"
How do I fix this? I can't even do sudo apt-get remove jedit, or sudo apt-get upgrade.

---

### Post by meng on 2006-08-26
sudo dpkg -r jedit

---

### Post by mlie on 2006-08-26
It's alrite.. I've solved it.. Googled the error message and found a thread on this.
The magic command is: 
sudo dpkg --remove --force-depends --force-remove-reinstreq jedit
Phiuhhh...

---

### Post by meng on 2006-08-26
Congrats. By the way, you may be better off unpacking the java archive than using a .deb, although the .deb ought to be safe in this case, always prefer Ubuntu .debs rather than any old .deb

---

