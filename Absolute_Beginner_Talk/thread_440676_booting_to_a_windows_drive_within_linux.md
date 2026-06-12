---
title: "booting to a windows drive within linux"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by superwazn on 2007-05-11
how can i boot a windows drive after im already in ubuntu? do i have to use a virtual drive or whatever thats about? i want to be able to start up my windows drive without actually rebooting my machine. how can i get this done?
thanks for any and all of your help:)

---

### Post by aysiu on 2007-05-11
You would have to use VMWare or something like it.

Try this:
[Run Existing Windows Installation on Ubuntu with Vmware Player](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

---

### Post by veloce on 2007-05-14
> **superwazn said:**
> how can i boot a windows drive after im already in ubuntu? do i have to use a virtual drive or whatever thats about? i want to be able to start up my windows drive without actually rebooting my machine. how can i get this done?
thanks for any and all of your help:)

It's a little unclear what you mean by a "windows drive".  Do you have a dual boot system that has a windows installation on it? If so, you can run that installation of windows as a virtual machine under ubuntu.  HOWEVER, there are a number of issues with doing this - for one thing it really confuses M$'s hardware check for legal installs of windows. It works best if you choose not to go back to booting windows. (I.e. disable the dual boot and always run windows using the virtual machine software).

If you have a fully ubuntu system and want to run windows, then you can create a fully virtual windows install.  The "hard disk" will be a file in  your ubuntu file system - only readable by the virtual machine software.

---

