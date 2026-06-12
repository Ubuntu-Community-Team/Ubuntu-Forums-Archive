---
title: "help w/ vmware install asap please"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by jeff00z28 on 2007-05-15
I cannot get vmware to install in abuntu 7.4. I am at work and was instructed to install ubuntu and hten install vmware so that there can be a virtual windows xp machine on it. I am pretty new to linux. When I downloaded the tars (I tried server, virtual machine, and player) I click the install.nl file and it says it cannot be found and it may have been deleted. I tried extracting them too. I tried tutorials where you use all command line methods but that showed the same problem.  Please help me if you can. I installed the kde desktop and am running that if that makes it any different.

---

### Post by veloce on 2007-05-16
> **jeff00z28 said:**
> I cannot get vmware to install in abuntu 7.4. I am at work and was instructed to install ubuntu and hten install vmware so that there can be a virtual windows xp machine on it. I am pretty new to linux. When I downloaded the tars (I tried server, virtual machine, and player) I click the install.nl file and it says it cannot be found and it may have been deleted. I tried extracting them too. I tried tutorials where you use all command line methods but that showed the same problem.  Please help me if you can. I installed the kde desktop and am running that if that makes it any different.

vmware server can now be installed from the Ubuntu repositories.  I used Synaptic package manager.

Before you start, get a serial number from vmware.com.  Then add the commercial repository to your list:

Use Alt+F2 to bring up the run command window, enter:
```
gksudo gedit  /etc/apt/sources.list

```
To edit the apt sources config file.

Add the line:
```
deb http://archive.canonical.com/ubuntu feisty-commercial main

```

Then run Synaptic package manager, update the files list, search for vmware, and install vmware-server.  At some stage it will ask for the serial number you got before.

vmware server console will be in the Applications-System Tools menu.

---

### Post by steveneddy on 2007-05-16
I did that and it won't start for me.

Any answers?

---

### Post by dynacrylic on 2007-05-16
Have you looked at this guide? 
   [http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

I used the howtoforge to install vmware on Kubuntu 6.10 and it was a breeze.

---

### Post by veloce on 2007-05-17
> **steveneddy said:**
> I did that and it won't start for me.

Any answers?

You did what exactly?

Did anything unexpected happen while doing it?

What happens when you try and start it?

Try starting it from a terminal (the command is "vmware").  What messages do you get?

---

