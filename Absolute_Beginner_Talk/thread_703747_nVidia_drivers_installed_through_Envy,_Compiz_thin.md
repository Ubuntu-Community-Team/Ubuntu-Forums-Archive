---
title: "nVidia drivers installed through Envy, Compiz thinks I need to install &quot;restricted dr"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by jeepfreak2002 on 2008-02-21
Compiz is confused.  It thinks that I still need to install the generic "restricted driver" that Ubuntu suggests, but I have already installed the driver through Envy, and have been happily playing Guild Wars for an hour.  

How do I get Compiz to realize that the drivers are enabled??

Thanks!!

---

### Post by pedro_orange on 2008-02-22
What does it say about your driver in the Restricted Drivers management tool?
I presume it will be enabled.

Envy is a great tool, but I've always found it better off to use the Restricted Drivers tool to install my graphics drivers.

---

### Post by Malta paul on 2008-02-22
Now that you have installed the driver with Envy, check that your restricted driver is also enabled.
Have fun:)

---

### Post by Sceiron on 2008-02-22
You may wanna try to find the reason for the problem, 
it would be informativ if u could paste the output from teminal of:

```
cat /etc/X11/xorg.conf
```
This will tell what driver is recogniced by your Xwindow system. (somewhere in here)


```
glxinfo
```
This will probably give some hints about/if the system has (if any) problems with the OpenGL librarys.


```

glxinfo | grep &#8216;direct rendering&#8217;

```
this will tell if your system has 3D rendering enabled.

---

