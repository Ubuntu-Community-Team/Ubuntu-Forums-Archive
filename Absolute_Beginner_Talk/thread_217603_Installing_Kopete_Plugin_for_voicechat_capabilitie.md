---
title: "Installing Kopete Plugin for voice/chat capabilities"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by Dinerty on 2006-07-17
Right Im trying to install konference-0.1alpha2.tar.gz

 I installed "build-essential" packages and extracted konference-0.1alpha2.tar.gz

 1. Opened Terminal
 2. Located the extracted konference-0.1alpha2 directory
 3. ```
./configure
``` in the directory

 4. Then recieved this:


             ```
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!
```
   
 I'm not sure where it's installed and how to resolve this problem :(


Thanks

---

### Post by quick_dudley on 2007-12-07
```
sudo apt-get build-dep kopete
```

---

