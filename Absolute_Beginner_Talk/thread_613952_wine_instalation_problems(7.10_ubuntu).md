---
title: "wine instalation problems(7.10 ubuntu)"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by White-Wolf52 on 2007-11-15
hi, trying to install wine on Ubuntu 7.10, using the synaptic package manager, comes up with the error "wine:
 Depends: libaudio2  but it is not installable"
any help would be appreciated

---

### Post by markharding557 on 2007-11-15
are you installing a ubuntu wine deb?
have you got all repositories enabled?

---

### Post by Buster95 on 2007-11-20
Hello,
I have the same problem with libaudio2.

Regarding your question, my Synaptic Package Manager can find only a non-Canonical endorsed deb package. I have all repositories enabled.

I also unsuccessfully tried to load it directly via the terminal (see below)

dexter@HOME-DESKTOP:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libaudio2 but it is not installable
E: Broken packages
dexter@HOME-DESKTOP:~$

---

### Post by Buster95 on 2007-11-21
> **Buster95 said:**
> Hello,
I have the same problem with libaudio2.

Regarding your question, my Synaptic Package Manager can find only a non-Canonical endorsed deb package. I have all repositories enabled.

I also unsuccessfully tried to load it directly via the terminal (see below)

dexter@HOME-DESKTOP:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libaudio2 but it is not installable
E: Broken packages
dexter@HOME-DESKTOP:~$

Update:
Don't know how, but it now works. I de-selected ALL Synaptic sources, shut down, re-started then re-selected the same Synaptic sources. Re-ran the Synaptic update and the Wine installation and it just started working!!

Cheers

---

### Post by markharding557 on 2007-11-21
you can get the most recent wine version here
[http://www.winehq.org/site/download]("http://www.winehq.org/site/download")

---

