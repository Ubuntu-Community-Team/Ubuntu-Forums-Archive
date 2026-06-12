---
title: "Need some help with VirtualBox"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by uruk912 on 2008-02-11
When i try to install it i get this:
[IMG]http://i27.tinypic.com/mbof2v.png[/IMG]

Will some one tell me why i get this?

---

### Post by uruk912 on 2008-02-11
Bump
someone please answer this.

---

### Post by jan quark on 2008-02-11
try to download via the synaptic packet manager and see if this works

---

### Post by Incense on 2008-02-11
Did you already try to install virtual box from the repos? If so maybe you should uninstall that version through synaptic, and then try to install the .deb. Just a guess though.

---

### Post by pytheas22 on 2008-02-11
take a look at [http://ubuntuforums.org/showthread.php?t=663762](http://ubuntuforums.org/showthread.php?t=663762), looks similar to your problem.

---

### Post by uruk912 on 2008-02-11
Alright well thats fixed but now i have another problem:
[IMG]http://i26.tinypic.com/5efxgo.png[/IMG]

---

### Post by pytheas22 on 2008-02-11
is the virtualbox-ose-modules package really not installed?  If so, try installing it.  If it actually is installed, try rebooting, or use modprobe -l to try to figure out if the module is loaded or not.  I don't know exactly what the module's called but I believe that it's obvious, or you could probably figure it out by searching online.

---

### Post by uruk912 on 2008-02-11
Ive been looking on line and nothing it telling me a stright answer. I got past this part and now all i need to do is this i remember seeing it some where but i forget here some one take a look at this:

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by pytheas22 on 2008-02-11
yeah, you have to add yourself to the vboxusers group in order to start the machine, because of permissions issues.  I don't know how to do that so I always just run it as root and it works fine.  Open a terminal and type "sudo VirtualBox" and you should be good.

---

### Post by Zero Prime on 2008-02-11
> **uruk912 said:**
> Alright well thats fixed but now i have another problem:
[IMG]http://i26.tinypic.com/5efxgo.png[/IMG]

I'll give you the easiest answer for your problem.  Open terminal then highlight the blue colored text that the warning tells you to enter into the terminal, minus the quotations of course.  Now paste this into terminal and hit enter.  Your problem should be fixed now.  I have to do this everytime I've installed VB.

Also, as pytheas22 said, you will have to go into users and groups and add yourself to the VBox group and then reboot your system.

---

### Post by uruk912 on 2008-02-11
Well u where right i needed to run it in "sudo" so yeah solved my problem but along the way i found another progam called Wine is this program any good?

---

### Post by pytheas22 on 2008-02-11
yeah, wine is a very useful and interesting program.  Its aim is to run Windows binaries without any kind of emulation, and when it works it's ideal because you don't waste any resources on emulation, and everything is nicely integrated with your native Linux system.  In reality, however, a lot of Windows programs don't work under wine, and sometimes those that do can behave strangely.  Basically the wine project is trying to reverse-engineer the entire Windows operating system, which is not a simple task.

If you only need to run one specific program, try looking it up at [http://appdb.winehq.org/](http://appdb.winehq.org/) to see how well it works.  Wine is definitely a better alternative than a virtual machine if you can get it to do what you need.

---

### Post by uruk912 on 2008-02-11
Yeah i got it accadently before and i wasnt sure what it did thanks. THANKS TO EVERYONE FOR HELPING ME PROBLEM SOLVED

---

