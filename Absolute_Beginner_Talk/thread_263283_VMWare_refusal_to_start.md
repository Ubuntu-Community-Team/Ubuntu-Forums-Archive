---
title: "VMWare refusal to start"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by Rush_898 on 2006-09-22
So I had vmware installed, using it for the few XP things I need.  Now It won't seem to start if I click on it the program shows up on the bottom bar and then just dies, no error message, no nothing.  So in reading this article
[URL="https://help.ubuntu.com/community/VMware_Guide%3a_Installing_VMware_Server_on_Ubuntu_6%2e06_LTS_amd64?highlight=%28vmware%29"]
Troubleshooting VMware[/URL]

I figure it is maybe that it needs to be recompiled after an update, but when I try the suggested steps for if VMWare refuses to start I get this:

chase@chase-desktop:~$ sudo apt-get install linux-headers`uname -r`
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers2.6.15-27-amd64-generic
chase@chase-desktop:~$ sudo rm /usr/src/linux
rm: cannot remove `/usr/src/linux': No such file or directory
chase@chase-desktop:~$


Any ideas?

---

### Post by reacocard on 2006-09-22
> **Rush_898 said:**
> So I had vmware installed, using it for the few XP things I need.  Now It won't seem to start if I click on it the program shows up on the bottom bar and then just dies, no error message, no nothing.  So in reading this article
[URL="https://help.ubuntu.com/community/VMware_Guide%3a_Installing_VMware_Server_on_Ubuntu_6%2e06_LTS_amd64?highlight=%28vmware%29"]
Troubleshooting VMware[/URL]

I figure it is maybe that it needs to be recompiled after an update, but when I try the suggested steps for if VMWare refuses to start I get this:

chase@chase-desktop:~$ sudo apt-get install linux-headers`uname -r`
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers2.6.15-27-amd64-generic
chase@chase-desktop:~$ sudo rm /usr/src/linux
rm: cannot remove `/usr/src/linux': No such file or directory
chase@chase-desktop:~$


Any ideas?


Needs to be
```
sudo apt-get install linux-headers-`uname -r`
```
(you forgot the dash)

then do
```
sudo vmware-config.pl
```

Hope this helps!

---

### Post by aktiwers on 2006-09-22
Hey it worked for me!
The same thing happend to my Vmware, after installing the latest updates to dapper.

Thanks!

---

### Post by Rush_898 on 2006-09-22
Worked like a charm, thanks!

---

### Post by jwalker on 2006-09-24
This has just happened to me, pretty much for the second time, I know this solution will work, so thanks again. As a n00b and for the sake of others, why does this keep happening? What are the updates doing to my VMWare setup? Should I not download updates in the future, or should I remember to run the sudo apt-get install linux-headers-`uname -r` command? Oh crap, see? Just as I type this the 'Software updates available' balloon has appeared? I quake with fear, what does it want to update this time? :-/

Thanks in advance, having the solution is great, but avoiding the situation is > than. 

Cheers

Chris

---

### Post by reacocard on 2006-09-24
> **jwalker said:**
> This has just happened to me, pretty much for the second time, I know this solution will work, so thanks again. As a n00b and for the sake of others, why does this keep happening? What are the updates doing to my VMWare setup? Should I not download updates in the future, or should I remember to run the sudo apt-get install linux-headers-`uname -r` command? Oh crap, see? Just as I type this the 'Software updates available' balloon has appeared? I quake with fear, what does it want to update this time? :-/

Thanks in advance, having the solution is great, but avoiding the situation is > than. 

Cheers

Chris

It happens because VMWare depends on a kernel module. This has to be custom-built for whatever kernel you're running, so whenever the kernel is updated, the module no longer works and has to be rebuilt for the new kernel.

It's a good idea to keep your kernel up-to-date. There are also "linux-headers-XXX" metapackages that will save you the trouble of getting "linux-headers-'uname -r'" every time. You'll just have to run "sudo vmware-config.pl" to rebuild the modules.

---

