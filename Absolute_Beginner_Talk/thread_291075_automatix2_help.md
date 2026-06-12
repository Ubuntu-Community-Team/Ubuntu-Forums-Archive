---
title: "automatix2 help"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-11-02
Here's some output I'm getting while trying to install automatix2...
root@monte:/home/monte # apt-get -f install automatix2
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  automatix2: Depends: tango-icon-theme-common but it is not installable
              Depends: python-vte but it is not installable
              Depends: python-gnome2-extras but it is not installable
E: Broken packages

How can I fix this? I downloaded the dependencies but they won't install. It says permission denied. I need something a little more intuitive to do this, I'm too new to this stuff!!;)

---

### Post by NeoLithium on 2006-11-02
To fix the broken packages, you just need to open up Synaptic Package Manager, go to Edit, and select Fix Broken Packages.

---

### Post by saintj0n on 2006-11-02
This is a fresh install. How come I have broken packages anyway?:-k

---

### Post by RudolfMDLT on 2006-11-02
Hi,

sudo dpkg --configure -a

then

sudo apt-get install -f

This should work. Post back if it doen't.

Cheers!

---

### Post by saintj0n on 2006-11-02
Here is the output:


monte@monte:~$ sudo -s
root@monte:~# dpkg --configure -a
root@monte:~# apt-get install -f
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@monte:~# apt-get install -f automatix2
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  automatix2: Depends: tango-icon-theme-common but it is not installable
              Depends: python-vte but it is not installable
              Depends: python-gnome2-extras but it is not installable
E: Broken packages
root@monte:~#

Pretty much the same situation...

---

### Post by Kieranties on 2006-11-02
Have you followed the instructions [over here]("http://getautomatix.com/wiki/index.php?title=Installation") fully?

---

### Post by RudolfMDLT on 2006-11-02
Is the -f necessary? I’m not at an ubuntu machine right now to test so this is more a question than a answer.  I’ve never used it before?

---

### Post by Kieranties on 2006-11-02
It is, as it basically fixes things up for you!

[QUOTE=the man page]-f, --fix-broken
              Fix; attempt to correct a system with broken dependencies in place. This option, when used with install/remove, can omit any packages to permit APT to deduce a  likely  solution.
              Any  Package that are specified must completely correct the problem. The option is sometimes necessary when running APT for the first time; APT itself does not allow broken pack&#8208;
              age dependencies to exist on a system. It is possible that a system’s dependency structure can be so corrupt as to require manual intervention (which  usually  means  using  dse&#8208;
              lect(8)  or  dpkg  --remove  to  eliminate  some  of  the  offending  packages).  Use of this option together with -m may produce an error in some situations. Configuration Item:
              APT::Get::Fix-Broken.
[/QUOTE]

---

### Post by rivera82 on 2007-11-04
What i did was go to "System/Administration/Software Sources" and checked the unchecked boxes, after that ```
sudo apt-get install automatix2
```

---

### Post by housam on 2007-11-06
> **rivera82 said:**
> What i did was go to "System/Administration/Software Sources" and checked the unchecked boxes, after that ```
sudo apt-get install automatix2
```

This way work as a flash. thanks for the advice.:)

---

### Post by dima86 on 2007-12-28
Hi. I have the same problem, and i tried following all the possible instruction, and fixing the broken packages and the box ticking, but nothing is working with me. is there anything else that i might do?

---

### Post by overdrank on 2007-12-28
> **dima86 said:**
> Hi. I have the same problem, and i tried following all the possible instruction, and fixing the broken packages and the box ticking, but nothing is working with me. is there anything else that i might do?

Hi and welcome,  automatix is not recommended here. What are the errors you receive and what are you trying to install.

---

### Post by zvacet on 2007-12-28
```
sudo apt-get remove --purge automatix2
```

You don´t need it,belive me.If you need something to install and you don´ know how just post here and somebody will tell you.

---

