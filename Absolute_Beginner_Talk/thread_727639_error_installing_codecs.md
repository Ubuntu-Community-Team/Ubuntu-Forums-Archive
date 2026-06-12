---
title: "error installing codecs"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by shleusink on 2008-03-18
I was trying to install the ubuntu-restricted-extras when something happened, not sure what.

I tried again and got this message;

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

.....so now what do I do?

---

### Post by oedha on 2008-03-18
open terminal
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras

---

### Post by shleusink on 2008-03-18
Thanks for the quick reply, 

now this happens after I did the last command, this means nothing to me, is it a problem?


The following packages have unmet dependencies:
  sun-java6-bin: Depends: sun-java6-jre (= 6-03-0ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by Neo0351 on 2008-03-18
```
sudo apt-get -f install
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by shleusink on 2008-03-18
why does it stall out on this screen?  ** see attached pic **

---

### Post by Neo0351 on 2008-03-18
Hummm, you should be able to select ok and complete the install.  Try installing sun-java6-jre from synaptic.

---

### Post by oedha on 2008-03-18
did your system updated ?
just click ok for that window
to make your system update :==> sudo apt-get install upgrade
:)

---

### Post by shleusink on 2008-03-18
Just tried the update and got

leusink@leusink-laptop:~$ sudo apt-get install upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package upgrade

---

### Post by Neo0351 on 2008-03-18
> sudo apt-get install upgrade

It should be

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by oedha on 2008-03-18
uppsss.....sorry......
suppose to be :==> sudo apt-get upgrade
:D

---

### Post by shleusink on 2008-03-18
thanks again for your help...

for some reason when I type in <sudo apt-get upgrade> I get to this part:

[COLOR="Navy"]leusink@leusink-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  sun-java6-bin sun-java6-jre
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/32.7MB of archives.
After unpacking, 93.6MB of additional disk space will be used.
Do you want to continue [Y/n]? 
[/COLOR]

Then I hit 'y' then 'enter' and it hangs up every time on the blue screen I attached earlier

---

### Post by Neo0351 on 2008-03-18
Did you try synaptic to install java 6?

---

### Post by shleusink on 2008-03-18
yeah.....   no.

Works like a charm then.

Thanks

---

### Post by Neo0351 on 2008-03-18
No problem.

---

