---
title: "Synaptic problem"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by cosmo18 on 2007-04-09
anytime I install anything using synaptic package manager it attemps to install the VMware player and fails then whenever I restart I have to reinstall the NVIDIA driver to be able to boot into kubuntu. How can I fix this?

---

### Post by kazuya on 2007-04-10
have you tried closing synaptic first.
Click undo> in synaptic>

go to terminal>

sudo apt-get update

   then enter password


sudo apt-get upgrade

    then enter password if prompted for it.



For solution 2: Are you using dapper LTS, feisty 7.04, or edgy 6.10?

Is VMware installed already or did you do something where you forced install and VMware was a dependent package? i.e you used dpkg force - something...

Could also be that whenever, you attempt to install, the app you are installing wants to remove or does remove nvidia drivers already installed...

What are you trying to install that causes this?

---

