---
title: "the old dependencies troubles :("
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by pedrotuga on 2006-04-19
```
root@isr-dhcp-2:~#  sudo apt-get install libmysqlclient14-dev
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
  libmysqlclient14-dev: Depends: libmysqlclient14 (>= 4.1.10a-2ubuntu0.1) but it is not going to be installed
                        Depends: zlib1g-dev but it is not going to be installed
```


ok... how do i solve this dependencies problems... i only have text mode access to this computer

---

### Post by nalmeth on 2006-04-19
I would go:
sudo apt-get -f install
sudo apt-get install zliblg-dev libmysqlclient14

---

### Post by mostwanted on 2006-04-19
Try using Synaptic instead.

---

### Post by aysiu on 2006-04-19
[QUOTE=mostwanted]Try using Synaptic instead.[/QUOTE] Synaptic is just a graphical front-end for *apt-get*. It won't make a difference.

I would advise getting a new sources.list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Dependency problems usually arise from conflicting repository sources.

---

### Post by pedrotuga on 2006-04-19
dam... is not working :(

it pops up more and more dependencies :(

i will give it a try with an updated sources... wich i think mine is, but... anyway

---

### Post by nalmeth on 2006-04-19
I don't know if it is a good idea to just get a different sources.list
try
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get -f install

---

