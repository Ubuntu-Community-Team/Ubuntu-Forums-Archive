---
title: "change /usr directory ownership back to root"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by findik1 on 2007-09-11
Hi

For some software installation I changed /usr directory ownership (with chown) from root to myuser. Now package manager does not work: it says " Su retuned wit error". How can I go back to set /usr directory to set it to root. When I tried:

~$ sudo chown -R /usr root

I got

sudo: must be setuid root

thank you,
findik

---

### Post by dwhitney67 on 2007-09-11
You were damn close.  The proper syntax is:

[FONT="Courier New"]$ sudo chown -R root:root /usr [/FONT]

If this still fails, then

[FONT="Courier New"]$ su
< enter root password >
# chown -R root:root /usr[/FONT]

---

### Post by findik1 on 2007-09-11
> **dwhitney67 said:**
> You were damn close.  The proper syntax is:

[FONT="Courier New"]$ sudo chown -R root:root /usr [/FONT]

If this still fails, then

[FONT="Courier New"]$ su
< enter root password >
# chown -R root:root /usr[/FONT]

It failed: 
It gaves the following output

$ sudo chown -R root:root /usr
sudo: must be setuid root


I dont have a root paswd. I have sudo pswd but it does not accept it.

---

### Post by findik1 on 2007-09-11
I found this thread to solve the issue of setuid:

[http://ubuntuforums.org/showthread.php?t=536706&highlight=setuid+root](http://ubuntuforums.org/showthread.php?t=536706&highlight=setuid+root)

but still not sure howto set /usr Owner as root

---

### Post by findik1 on 2007-09-11
> **findik1 said:**
> I found this thread to solve the issue of setuid:

[http://ubuntuforums.org/showthread.php?t=536706&highlight=setuid+root](http://ubuntuforums.org/showthread.php?t=536706&highlight=setuid+root)

but still not sure howto set /usr Owner as root


this simply solves the issue:  /usr Owner root

[http://ubuntuforums.org/showthread.php?t=495754&highlight=setuid](http://ubuntuforums.org/showthread.php?t=495754&highlight=setuid)


I still cannot open my snaptic package manager!!!!!
it says Su returned with error!

---

### Post by trak87 on 2007-09-11
Synaptic is not in /usr/bin, it's in /usr/sbin . 

Additionally, most permissions in /usr/bin are root:root, but not all. 

Don't ever change the ownership of system directories like that.

---

### Post by Yes on 2007-09-11
I had the same problem, [here](http://ubuntuforums.org/showthread.php?t=528103).

---

