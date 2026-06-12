---
title: "javac path problems"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by Silver-revo on 2006-04-25
:confused: 

I am trying to get javac to run everywhere.
I think that I have figured out the export command,
> export PATH="$PATH:/jdk50/bin
thats the general idea from what I have found but how do you add it to your bash.Profile?

I can't even find the bash.profile let alone edit it...

---

### Post by Silver-revo on 2006-04-25
also one more problem that probobly fits in here somewhere,
my shell no longer produces the path at the end > clyde@PortableMAGIK:~$ ls


instead of > PortableMAGIK:/home/

---

### Post by auroraborealis on 2006-04-25
It's either ~/.bash_profile or ~/.bashrc or /etc/profile (for systemwide). You could also do `sudo update-alternatives --all` and find all instances of Java.

For bash prompts, check [http://www-128.ibm.com/developerworks/library/l-tip-prompt/](http://www-128.ibm.com/developerworks/library/l-tip-prompt/)

---

