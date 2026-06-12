---
title: "[SOLVED] Installing Kernels"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by orionstar on 2008-04-01
Hello. I do realize there are posts already for this, but I am a complete, and I stress COMPLETE beginner at Ubuntu and Linux in general. 

History/reasons aside, I need to compile kernel 2.6.20 on the current version of Ubuntu (7.10). 

I've looked on various sites, but they don't seem to be addressing people that are complete newbies to the linux scene.

I try to follow along, but when I get stuck/receive errors, there's nothing I can do about it than to try looking for other sites that go about it another way.

Using the guide given here: [http://www.debianhelp.co.uk/kernel2.6.htm](http://www.debianhelp.co.uk/kernel2.6.htm) I got stuck on the first line where it says to install this: #apt-get install kernel-package ncurses-dev fakeroot wget bzip2

The error I get is as follows:
root@daniel-desktop:~# apt-get install kernel-packages ncurses-dev fakeroot wget bzip2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kernel-packages
root@daniel-desktop:~# 

I would follow the rest, but I'm sure the last line (E: Couldn't find package... etc) shouldn't appear. 

Please help! I happen to be a second-year among a class of third-years, and I'm completely lost and confused as to what to do when at a problem like this.

---

### Post by Slushdoot on 2008-04-01
What features specific to Gutsy (7.10) do you need?  Feisty (7.04) came with 2.6.20 out-of-the-box so I think it'd be much easier to use that since it's guaranteed not to break anything. :)

EDIT: I think the above would be a nice way to sidestep the issue but, failing that, the package that isn't installing is actually called **kernel-package** not kernel-package[size=3]**s**[/size].  It's looking for "packages" and can't find it so it's returning an error.

---

### Post by orionstar on 2008-04-01
It's nothing specific to the latest version - it's just that the course involves fiddling around with the kernel - and if by mistake something breaks, then there's a backup kernel so the system itself won't break (was the explanation given).

I've tried the way before - still doesn't seem to work.

root@daniel-desktop:/home/daniel# apt-get install kernel-package ncurses-dev fakeroot wget bzip2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kernel-package

---

### Post by Slushdoot on 2008-04-01
Interesting.  I just tested it myself and it installed without issue with
sudo apt-get install kernel-package
which is just what you ran.  

```
slushdoot@Monaco:~$ sudo apt-get install kernel-package
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev gettext intltool-debian patch po-debconf
Suggested packages:
  debian-keyring cvs gettext-doc linux-source kernel-source libdb3-dev
  libncurses-dev docbook-utils diff-doc
Recommended packages:
  libc6-dev libc-dev libmail-sendmail-perl
The following NEW packages will be installed:
  dpkg-dev gettext intltool-debian kernel-package patch po-debconf
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 2470kB of archives.
After unpacking 10.2MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

Hmm...

---

### Post by orionstar on 2008-04-02
Is there a command I need to do to update the apt-get packages?

---

### Post by Tatty on 2008-04-02
> **orionstar said:**
> Is there a command I need to do to update the apt-get packages?

```
sudo apt-get update
```  or omit the sudo if you are using su / in recovery console

---

