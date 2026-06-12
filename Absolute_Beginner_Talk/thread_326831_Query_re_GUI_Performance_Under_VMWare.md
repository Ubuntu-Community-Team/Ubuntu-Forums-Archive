---
title: "Query re GUI Performance Under VMWare"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by bob.flem1ng on 2006-12-28
Hi,

I installed Ubuntu 6.06 LTS as a virtual machine running under VMWare Server. The install works OK so far but I am not convinced the GUI performance is as good as it could be. For instance, when dragging windows around the desktop the movement is very choppy. And in some windows, especially those for certain games, just moving the mouse accurately is impossible due to the lag between moving the mouse and the pointer moving on screen. 

I've had a look through the menu structure for an option that would let me confirm the video settings, to no avail.

I realise this is a bit of a finger-in-the-air type question but any comments would be welcome. 

My hardware spec is Intel 6700 dual core 2.66ghz, 2G ram, 512mb X1900XT graphics.

Thanks in advance.

---

### Post by OffHand on 2006-12-28
Did you install vmware tools?

---

### Post by bob.flem1ng on 2006-12-28
I tried, but gave up when the installer started asking about locations of kernel header files. I was hoping I wouldn't have to get my hands that dirty.

---

### Post by jonathan.lees on 2006-12-28
cough.. xcuse me bob...cough..splutter did you just try the default locations it was asking for?

---

### Post by bob.flem1ng on 2006-12-28
Scratch that, I have now installed vm tools, albeit without the shared folders and ast networking functionality. But I see no improvement in the GUI performance.

---

### Post by veloce on 2007-02-18
I've found the best gui performance from virtual machines was to use rdp, in full screen mode, to the vm.  I started doing this when the vms were on a different machine and continued with them on the same machine.  

It does require that you have some network running between the host and vm, I use host only networking.

Also note, I am using vmware server not player. YMMV.

---

