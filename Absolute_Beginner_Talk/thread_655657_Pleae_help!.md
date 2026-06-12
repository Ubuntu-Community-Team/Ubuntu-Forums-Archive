---
title: "Pleae help!"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by lohnew on 2008-01-01
I love ubuntu, but ireallly want to try out gOS...i have innotek virtualbox installed on my system and want to install gos using that program, can i get some help on how to do that? and how to make instalation cd of GOS?

---

### Post by (((X))) on 2008-01-01
you already got an image, right?
Insert cd/dvd, double click on your image, ubuntu will probably burn it automatically as an image.
You do know how to use virtualbox?

---

### Post by blithen on 2008-01-01
You don't even have to make an installtion CD unless you want to put on your system. Just fire up virtual box make a new virtual machine.
Then on the right side there should be a few options click on CD/DVD-ROM
And that will bring up a menu click 'Mount cd/dvd drive'
Then select ISO image then find where you put the iso image at.

---

### Post by lohnew on 2008-01-02
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}



thats what happend when i mounted it to the iso..**.can i get some info on how to set up the virtual michene the right way for gOS?** I am a real noob.

---

### Post by (((X))) on 2008-01-02
so, you installed virtualbox..
first you need to know what kernel gOS is using..I assume its version is 2.6
start vistualbox, click on new, then select os type, linux 2.6 give it a name.
Base memory size itn't interesting..next click on new, to attash a virtual disk.
To make your virtualbox boot from image, click on settings, go to cd/dvd and check mount cd/dvd drive and iso mage box..browse for your gos image.

That's it..

---

### Post by p_quarles on 2008-01-02
> **(((X))) said:**
> so, you installed virtualbox..
first you need to know what kernel gOS is using..I assume its version is 2.6
start vistualbox, click on new, then select os type, linux 2.6 give it a name.
Base memory size itn't interesting..next click on new, to attash a virtual disk.
To make your virtualbox boot from image, click on settings, go to cd/dvd and check mount cd/dvd drive and iso mage box..browse for your gos image.

That's it..
+1

First, though, the OP will have to add the user to the Virtualbox group:
```
sudo adduser *yourusername* vboxusers
```
Hit ctrl-alt-backspace to logout, then log back in.

---

### Post by lohnew on 2008-01-02
p_quarles solved it, Thanks!

---

