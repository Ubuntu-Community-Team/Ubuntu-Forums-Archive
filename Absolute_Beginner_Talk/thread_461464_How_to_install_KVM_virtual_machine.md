---
title: "How to install KVM virtual machine?"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by acutu on 2007-06-01
Hi, I am new to Ubuntu and want to use it as a host to run open source KVM virtual machine which I will use to run both Windows XP which I am gradually migrating from and Kubuntu simultaneously. I have tried to follow the instructions on the KVM website 
[http://kvm.qumranet.com/kvmwiki/HOWTO](http://kvm.qumranet.com/kvmwiki/HOWTO)
but for a newbie like me, it is not sufficiently step-by-step to succeed. I have downloaded the Install file but do not understand how to either use Synaptic or the Terminal to install it. There are some instructions with a load of text, but just where I put the file I downloaded, or what I do with the text I don't know. I tried putting the .tar file on my desktop and also double clicked it and right clicked on the result and chose extract, and I copied the text in the instructions and pasted into the terminal, but it did not work. I am running 7.04 Feisty Fawn on an AMD Turion 64x2 laptop.
Please help, thanks.

#Resolved#

---

### Post by bodhi.zazen on 2007-06-01
LOL

Open a terminal.

Enter :

```
sudo aptitude install kvm
```

From there, see these links :

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by acutu on 2007-06-02
Thanks bodhi.zazen.
Making a little headway now, but stalling. The help info was a little bit helpful, but still hard for me to understand, a bit like a new language! I think stage 1 has been completed now at least.
I can now find kvm and kvm-source listed in the syaptic package manager as 'installed'.

I am next trying to open the kvm program, but cannot find it in my 'Applications' list.

I have still been trying to use the instructions in [http://kvm.qumranet.com/kvmwiki/HOWTO](http://kvm.qumranet.com/kvmwiki/HOWTO)
Q1. I presume that because the syaptic package manager lists kvm as installed, that I have completed stage 1 successfully and that I am having problems with stages 2 and 3 or maybe 2 has been completed succesfully, I don't know how to tell.
Q2. Do I need to copy the text as explained in the insructions for stages 2 and 3 exactly, or should I be substituting any of it for text which applies specifically to my situation please, in which case, which parts should I substitute please? 

Q3.1  When copying the instructions from the black text from the grey box and there is a next line, do I press the spacebar before going on to the next line or just carry on typing. I say this because the line lengths do not correspond with the line length of my terminal. 
Q3.2 I notice that in stage 3 the text on the second line is indented, does this indicate that the text on the second line starts by using the spacebar? Thanks and sorry to be so basic in my understanding.

---

### Post by acutu on 2007-06-02
Actually, thanks for your help, but I have had a change of plan. I am going to try:
[http://doc.gwos.org/index.php/VirtualBox#Introduction_.2F_FAQ](http://doc.gwos.org/index.php/VirtualBox#Introduction_.2F_FAQ)
as Virtual Box apparently is a bit further developed and has a complete tutorial for installation and doesn't even need to be installed through the terminal!

Thanks again,
A.C.

---

### Post by bodhi.zazen on 2007-06-02
LOL acutu !

Yea I would go with VirtualBox for now. KVM is more "bare metal" in that it is a command line application. I have not played with KVM as my hardware is not compatible.

KVM is based on qemu. So look at some qemu how-to's to learn the commands.

VirtualBox and VMWare are both easier to learn as they have nice gui's. VMWare is older (more developed, polished, and stable) and more full featrued, but IMO VirtualBox is quite nice.

VMWare : [http://doc.gwos.org/index.php/VMWareXP](http://doc.gwos.org/index.php/VMWareXP)

qemu : [https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

Use google to find more about qemu

---

### Post by acutu on 2007-06-03
Cheers bodhi.zazen
I tried to install Virtual Box but they haven't got a 64bit version yet. I might try forcing, which I have read about, but first I think I will try a force with something else, like Varicad demo for example, which is also not available yet in 64bit architecture.

Al C.

---

### Post by bodhi.zazen on 2007-06-04
> **acutu said:**
> Cheers bodhi.zazen
I tried to install Virtual Box but they haven't got a 64bit version yet. I might try forcing, which I have read about, but first I think I will try a force with something else, like Varicad demo for example, which is also not available yet in 64bit architecture.

Al C.

Virtualbox is due out with a 64 bit version soon, 1 week perhaps ?

[http://forums.virtualbox.org/viewtopic.php?t=281](http://forums.virtualbox.org/viewtopic.php?t=281)

---

