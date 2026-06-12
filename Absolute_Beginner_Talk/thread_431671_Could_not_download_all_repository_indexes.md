---
title: "Could not download all repository indexes"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by vnfatpig on 2007-05-03
When I reload the repository in Synaptic, I received this message:
```

http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz: Sub-process gzip returned an error code (1)
```

Would you please tell me why and how to fix this problem?

Thanks.

---

### Post by AtrejuT on 2007-05-03
this happens once in a while. it will probably be alright if you try again in a little while.

---

### Post by taurus on 2007-05-03
Or edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and remove the **us.** from all your repos.  Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by vnfatpig on 2007-05-03
@ taurus:

When I did as you shown, Synaptic show as below:

```
http://archive.ubuntu.com/ubuntu/dists/feisty-backports/main/source/Sources.bz2: MD5Sum mismatch
```

Would you please help me again, I waited so long but the server seem not funtioned properly.

Thanks in advance.

---

### Post by taurus on 2007-05-03
Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by vnfatpig on 2007-05-03
Here it is:

```
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://archive.ubuntu.com/ubuntu feisty main restricted 
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted

deb-src http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://archive.ubuntu.com/ubuntu feisty universe multiverse 
deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse

deb-src http://archive.ubuntu.com/ubuntu feisty universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security universe multiverse

# Ubuntu backports project
# GPG key: 437D05B5
deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse 

deb-src http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse


```

Thanks for your help :)

---

### Post by vnfatpig on 2007-05-04
Any help for me?

Thanks.

---

### Post by vnfatpig on 2007-05-04
Hello, would you please help me solving this problem?

---

### Post by taurus on 2007-05-04
Why don't you edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and comment out by placing a # in front of the **backports** repo, the last two lines.  Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by vnfatpig on 2007-05-05
Thank you so much, it solved my problem :)

---

