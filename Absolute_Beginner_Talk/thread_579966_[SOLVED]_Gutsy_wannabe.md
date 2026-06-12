---
title: "[SOLVED] Gutsy wannabe"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by nnjond on 2007-10-18
Hi,  I hope I'm bothering u with a simple prob:

I understand I can Upgrade Fiesty to Gutsy by downloading, following this procedure:

 sudo apt-get install -f
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

'fraid i don't know how to configure -a

---

### Post by overdrank on 2007-10-18
> **nnjond said:**
> Hi,  I hope I'm bothering u with a simple prob:

I understand I can Upgrade Fiesty to Gutsy by downloading, following this procedure:

 sudo apt-get install -f
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

'fraid i don't know how to configure -a

Hi you can just run that command in the terminal
```
sudo dpkg --configure -a
```

---

### Post by ThrobbingBrain66 on 2007-10-18
> **nnjond said:**
> Hi,  I hope I'm bothering u with a simple prob:

I understand I can Upgrade Fiesty to Gutsy by downloading, following this procedure:

 sudo apt-get install -f
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

'fraid i don't know how to configure -a

'sudo apt-get install -f' won't upgrade you to 7.10.  So after you you run the command overdrank gave you, check out this link:

[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

---

### Post by nnjond on 2007-10-18
Thanks for your help but...

nnjond@nnjond-desktop:~$ sudo dpkg --configure -a
Password:
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-00-2ubuntu2); however:
  Package sun-java6-bin is not installed.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-restricted-extras:
 ubuntu-restricted-extras depends on sun-java6-plugin; however:
  Package sun-java6-plugin is not configured yet.
dpkg: error processing ubuntu-restricted-extras (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-plugin
 ubuntu-restricted-extras
nnjond@nnjond-desktop:~$ 

What does this mean !

---

### Post by rug77 on 2007-10-18
Open your software installer (it's adept on Kubuntu, same on ubuntu ?) and type java in the search.  Look for the restricted extras and java 6 mentioned, and select and load them.

Then try again with the dpkg command.

Matt

---

### Post by nnjond on 2007-10-18
Thanks again.

The software installer in Fiesty seems to be 'Add/Remove programes'. when I try to open, I get:

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

---

### Post by overdrank on 2007-10-18
> **nnjond said:**
> Thanks again.

The software installer in Fiesty seems to be 'Add/Remove programes'. when I try to open, I get:

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

Hi could you post the out put of the command 
```
sudo gedit /etc/apt/sources.list

```

---

### Post by nnjond on 2007-10-18
Thanks for all your help. I think i've stumbled my way out of this (that ?) problem.

---

### Post by overdrank on 2007-10-18
> **nnjond said:**
> Thanks for all your help. I think i've stumbled my way out of this (that ?) problem.

Please post it  so that others may learn.  [-o<=D>

---

