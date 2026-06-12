---
title: "Running cpufreq-applet"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by thecow on 2007-02-03
I have downloaded a package update that included cpufreq-applet, I want to run it so that I can change the speed of my Pentium M cpu at will.  I have the applet downloaded, I can see the applet, it is a  .exe extension, but when I double click on it it does nothing.  I cant really imagine what I am doing wrong here.  Any help would be appreciated.

---

### Post by kevinlyfellow on 2007-02-03
I think this will help

Right click on an empty spot on your panels (I'm assuming your running gnome).  Choose 'Add to Panel...'  Then choose 'CPU Frequency Scaling Monitor'  It should then appear where you right clicked!

---

### Post by shareMenaPeace on 2007-02-03
Hi, 
"exe" means it is a windows executable.

You could use "wine" to try to run this windows program or get a linux program todo this.

---

### Post by wakady on 2007-02-03
exe files don't work on linux, its a executable win32 not on linux/unix

---

### Post by thecow on 2007-02-03
Ah, thanks.  Now I am having the problem of these cpu governors.  I want to make it so that my frequency cannot be automatically messed around with.  i.e If i set it at 800 MHZ, it stays permanently at 800, or 1.33 GHZ, it stays permanently at that.

---

### Post by kinematic on 2007-02-03
> **thecow said:**
> Ah, thanks.  Now I am having the problem of these cpu governors.  I want to make it so that my frequency cannot be automatically messed around with.  i.e If i set it at 800 MHZ, it stays permanently at 800, or 1.33 GHZ, it stays permanently at that.

uhmmm....why :confused: 
the powernow daemon handles ondemand scaling just fine.
if it raises the speed it's because the system needs the extra power.

---

