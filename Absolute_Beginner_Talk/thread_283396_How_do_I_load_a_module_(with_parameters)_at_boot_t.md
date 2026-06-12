---
title: "How do I load a module (with parameters) at boot time?"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-10-24
At commandline, I usually load moduleX manually with 

# modprobe moduleX mode=1

where mode=1 is the parameter that must be loaded with moduleX.

Google abit and it seems that adding the name of the module into /etc/modules will load the module at boot time. 

Is this the recommended method? Also, where do I put the parameter mode=1?

Thanks!

---

### Post by hw-tph on 2006-10-24
Add the name of the module to /etc/modules. This will load the module on boot.

Edit /etc/modprobe.d/options and add the options for your module:```
# Options for my own module
options module_name myparameter=1
```
"options" must be there, replace module_name with the actual name of the module and then just add the parameters. Read modprobe.conf(5) for more information (type **man 5 modprobe.conf**).

Håkan

---

### Post by Lucas[PL] on 2008-02-22
Hello 

Sorry for my English.

I have very similar problem but I think that I do all correctly....

I want load module "**dl2k**" with parameter jumbo frame.

I read that I have to use modprobe dl2k jumbo=1. This works...

But I don't want always do it manually....

I add line to **/etc/modprobe.d/options**  options dl2k jumbo=1.
And this also works. Because when I **rmmod dl2k** and **modporbe dl2k** with out parameter 
I have mtu=8000. But after system is reboot I still have mtu=1500.

What i did wrong ??

---

