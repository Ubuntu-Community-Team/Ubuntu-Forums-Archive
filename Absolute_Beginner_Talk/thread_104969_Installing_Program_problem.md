---
title: "Installing Program problem"
date: 2005-12-17
forum: Absolute Beginner Talk
---

### Post by SpLaTt on 2005-12-17
Apache~
First off i used the archive manager to extrat all the files to a desktop folder
went in the install file,
     $ ./configure --prefix=PREFIX
     $ make
     $ make install
     $ PREFIX/bin/apachectl start
"/usr/local/apache2" for PREFIX (did 2 times, one with no prefix, one with a prefix)

it looks like i got it all done right until the last step both times,

dmitri@Dmitri:~$ /usr/local/apache2/bin/apachectl start
bash: /usr/local/apache2/bin/apachectl: No such file or directory
dmitri@Dmitri:~$
&
dmitri@Dmitri:~$ sudo /usr/local/apache2/bin/apachectl start
Password:
sudo: /usr/local/apache2/bin/apachectl: command not found
dmitri@Dmitri:~$

also both times i went to look at the usr/local file, i didnt see a folder for apache

oh yeah, im installing apache to run a web server off linux,

one more thing, i just updated to 5.10, just wondering where the root terminal went? or do i just use sudo now?

---

### Post by kaamos on 2005-12-17
You are trying to install apache2? It is available in synaptic or by issuing the command```
sudo apt-get install apache2
``` in terminal

About sudo: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by SpLaTt on 2005-12-17
wow, thanks i am,
ubuntu has alot of things built into it, didint know that, thanks again

---

### Post by kaamos on 2005-12-17
You're welcome!
Almost every free program you might need can be installed with the package manager. See: [https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)

---

