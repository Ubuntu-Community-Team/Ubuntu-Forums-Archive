---
title: "Problem in installing MATLAB on Feisty"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by ayesha kalra on 2007-07-07
Hi all

I am experiencing problem in installing MATLAB on Ubuntu Feisty from CD-ROM. This is the error message I get

```
root@ak:/cdrom# ./install
bash: ./install: /bin/sh: bad interpreter: Permission denied
 
```

I tried installing by becoming the 'root' user but it did not help. Also 'sudo ./install' does not help either.

Any suggestions will be really helpful.

Thanks
Ayesha Kalra

---

### Post by taurus on 2007-07-07
Check the permissions of the _install_ on the CD.

```
ls -la
```
Otherwise, copy everything to your harddrive and change the permissions of install and run it from there.

---

### Post by ayesha kalra on 2007-07-07
Hi Taurus

ls -la gives 

```
-r-xr-xr-x 1 root root  39173 2006-02-06 14:35 install

```

I assume it means it is executable by the root user (or any user for that matter).

Ayesha

---

### Post by taurus on 2007-07-07
What does it look like then?

```
cat install
```

p.s.  Are you running x86 or x86_64?

---

### Post by TasKiNG on 2007-07-09
Thanks Taurus, I copied my CD to the hard disk and did a chmod -R 777 on the directory to make all files RWX.

It installed perfectly.

Also when installed you have to add 2 lines to the matlab/bin/matlab script for it to correctly run simulink and work with compiz / beryl. These are as follows :-

export AWT_TOOLKIT=MToolkit
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.00/jre/

( Thanks to Maximus for posting the above 2 lines )

Works a treat

---

