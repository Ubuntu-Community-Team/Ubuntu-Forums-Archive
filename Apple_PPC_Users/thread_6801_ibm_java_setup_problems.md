---
title: "ibm java setup problems"
date: 2004-12-01
forum: Apple PPC Users
---

### Post by rlpt on 2004-12-01
I have put the ibm java jdk on my powerbook and it almost works, the problem is that i couldn't download the rpm and so grabbed the tgz from some gentoo mirror, i installed it fine and it works but only if i run java from its directory, i can run java from another directory (i added /opt/IBMJava2-ppc-142/bin to my path) but if i do it dies because it can't find any java libraries, this is the problem.

cheers

rlpt

---

### Post by SyL on 2004-12-03
I don't understand why you want to download a tgz form a gentoo mirror.
 
 
 For add java to your path, put on your .bashrc
  ```

export JAVA_HOME="/opt/IBMJava2-ppc-142"
export PATH="$PATH:$JAVA_HOME/bin:$JAVA_HOME/jre/bin"
``` 
 It's not works on .bash_profile, don't ask me why I don't know.
 
  
 hope that will help you

---

### Post by cow_racer on 2004-12-04
I added the following lines to /etc/bash.bashrc

export JITC_PROCESSOR_TYPE=6
export JAVA_HOME=/opt/IBMJava2-ppc-142/
export PATH=$JAVA_HOME/bin:$PATH

It works fine for me.  For me without the
processor type, the VM would crash.

---

