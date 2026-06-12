---
title: "Problem with dependencies"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by edopizza on 2006-03-26
Hello 
I installed some unstable .deb packages with the command dpkg. After I discovered that there was the same package in stable version and installed it. 
"sudo apt-get -f install" and "System Update" would like to remove a huge quantity of packets. 
Now I get this error with dependencies when I try to update. 

The reported errors with dependencies are: 
  cpp-4.0: Depende: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.3-1 installed
  gij-4.0: Depende: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.3-1 installed
  libgcj6: Depende: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.3-1 installed

How can I remove the unstable packages and correct the wrong verson dependencies?

---

### Post by Xian on 2006-03-26
You need to downgrade those unstable packages.
This can be done using aptitude:

$ sudo aptitude install <pkgname>=<version>

However, this may not be possible due to recursive deps now on your system that are in place because of the unstable debs. You can also set your preferences in Synaptic to prefer a specific repository, and then try a system 'upgrade' in that environment.

---

### Post by edopizza on 2006-03-26
Thanks for your help. 
In fact the problem started because I installed packages from packages.debian.com instead of packages.ubuntu.com. 
With the right packages the problem solved and I learned to install only packages designed for ubuntu...

---

