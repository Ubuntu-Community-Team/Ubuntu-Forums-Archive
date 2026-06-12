---
title: "xmms install problem"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by Jonzo on 2006-04-09
Hello, I just installed Ubuntu today..  anyways, I was trying to install XMMS, and I get the following error:

jonzo@jonzo:~/Desktop$ cd xmms-1.2.10
jonzo@jonzo:~/Desktop/xmms-1.2.10$ sudo ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for prefix by checking for xmms... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
jonzo@jonzo:~/Desktop/xmms-1.2.10$


Can anyone help? thganks

---

### Post by Darkbird on 2006-04-09
ya, install build-essential

---

### Post by Sutekh on 2006-04-09
Why not install XMMS from the repositories.  No need to compile.

```
sudo apt-get install xmms
```

---

### Post by Jonzo on 2006-04-09
I did the apt-get method..and it worked - thanks very much

But I'd like to know, why didn't my first method work?

---

### Post by Qrk on 2006-04-09
Ubuntu doesn't come with c compilers by default. You have to install gcc through apt-get first. 

```
sudo apt-get install build-essential
```

This will get all of the stuff you need to compile from source, including gcc. Its a metapackage that makes sure everything works together.

---

### Post by Jonzo on 2006-04-09
jonzo@jonzo:~$ cd
jonzo@jonzo:~$ sudo apt-get build-essential
E: Invalid operation build-essential

:confused:

---

### Post by Jonzo on 2006-04-09
n/m forgot 'install' :)

---

### Post by Jonzo on 2006-04-09
Where can I view a list of available packages for install?

---

### Post by Sutekh on 2006-04-09
Open Synaptic (System -> Administration menu)

Or browse this link; [Ubuntu Packages](http://packages.ubuntu.com/)

---

### Post by Jonzo on 2006-04-09
thanks

---

