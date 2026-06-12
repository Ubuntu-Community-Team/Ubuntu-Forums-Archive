---
title: "[SOLVED] error message while trying to run virtual box"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by mangurt on 2007-12-31
Greetings all,
I am trying to run virtualbox and I am getting the following error.


Could not load the settings file '/home/ed/.VirtualBox/VirtualBox.xml' (VERR_OPEN_FAILED).
FATAL ERROR: Attribute 'LogHistoryCount' is not declared for element 'SystemProperties'
Location: '/home/ed/.VirtualBox/VirtualBox.xml', line 25, column 159.


Result Code: 
0x80004005
Component: 
VirtualBox
Interface: 
IVirtualBox {76b25f3c-15d4-4785-a9d3-adc6a462beec}

I have tried to remove the program and reinstall it, but to no avail, anyone have any idea on what I need to do to get this up and running?

Thanks

---

### Post by bump_ on 2007-12-31
Have you already installed an operating system in the virtual machine? Or is this before any sort of installation?

---

### Post by mangurt on 2007-12-31
This is before any installation.  I can't even get virtualbox to start up.

---

### Post by The Cog on 2008-01-01
IN that case, there is no harm in removing your VirtualBox settings directory and trying again. Open a command prompt and use the command:
**rm -rf .VirtualBox**
That will delete the offending settings file that its complaining about. 
IMPORTANT: There is no space between the dot and the V.
You can delete the directory with nautilus (the file manager) if you prefer - you just have to type Ctrl-H to enable seeing hidden files.

VirtualBox will create a new .VirtualBox directory full of default settings next time you run it.

---

### Post by mangurt on 2008-01-02
ding ding ding....we have a winner here.
Thanks!

---

### Post by jfdill_2 on 2008-01-09
> **The Cog said:**
> IN that case, there is no harm in removing your VirtualBox settings directory and trying again. Open a command prompt and use the command:
**rm -rf .VirtualBox**
That will delete the offending settings file that its complaining about. 
IMPORTANT: There is no space between the dot and the V.
You can delete the directory with nautilus (the file manager) if you prefer - you just have to type Ctrl-H to enable seeing hidden files.

VirtualBox will create a new .VirtualBox directory full of default settings next time you run it.

It seems to me that if you have any "machines" defined, that will also delete all of your virtual machines, might not be what people want if they are upgrading rather than a fresh install.  Wouldn't it be safer to just do:

rm -f ~/.VirtualBox/VirtualBox.xml

OK just tried this, you will also need to delete the ~/.VirtualBox/Machines/<machine name>/<machine name>.xml files.  Then you will need to add the existing virtual disks and create "New" machines, use the same old name and the devices etc should get picked up again.

---

