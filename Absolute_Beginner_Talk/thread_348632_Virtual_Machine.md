---
title: "Virtual Machine"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2007-01-29
Hi,

I recently installed an excellent program, VirtualBox, which allows me to run Windows XP (spit!!) within my Ubuntu environment.  Each time I start it, however, I get the following message...

   > 
   VirtualBox kernel driver not accessible, permission problem.

    At  [COLOR="Blue"]'/home/vbox/vbox/src/VBox/VMM/VM.cpp[/COLOR]' (303) in int   
    VMR3Create(void(*)(VM*, void*, int, const char*, unsigned int, const char*, const char*,  
    char*), void*, int(*)(VM*, void*), void*, VM**).

    VBox status code:- 1909 VERR_VM_DRIVER_NOT_ACCESSIBLE
    

To get round this problem I found this piece of text somewhere on these forums.  By typing the following code into the terminal VirtualBox works fine...

    > 
     sudo depmod
     sudo /etc/init.d/virtualbox start
     sudo chmod 666 /dev/vboxdrv
    

The problem with this method is that it is only temporary.  I have to keep the computer simple to use for other members of the family, so any help with solving this issue would be greatly appreciated.

---

### Post by mizar001 on 2007-01-29
depmod and chmod should be done once.
Starting virtualbox with the /etc/init.d/virtualbox start means that you are running it as service. So you should start this process at boot, as super user. 

That means that you cannot start virtual box as normal user. but maybe you can load a VM.

Probably your virtualbox is already started when you boot the machine. You have only to load the guest machine.

Do this :
Start your pc.
When you logged in try to see processes 
sudo ps -u yourLogin |grep virt
sudo ps -u root |grep virt

You should see some virtualbox service already running. Or not ?

---

