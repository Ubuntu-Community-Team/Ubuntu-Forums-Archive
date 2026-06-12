---
title: "[SOLVED] VMWare Sound Problem"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2007-07-29
Hello,

I'm using VMWare Player to use XP within Ubuntu. Everything works well except for the sound. There's none. My current soundcard is listed as HDA Intel under Ubuntu. What should I put in the config file so that VMWare/Windows XP finds it and uses it???

Thanks!

---

### Post by pollywog on 2007-08-05
Hey, sorry no one knew the answer to your question. I was using vmware player to run XP myself. In my case this provided a rather flawed interface between OS's. Mine seemed to randomly not mount USB devices, crash when I tried to mount the printer, and switch back and forth between recognizing my cd or dvd burner. I switched to Virtualbox, and couldn't be happier. Once installed thru synaptic, look in /opt/VirtualBox-1.4.0 to get the CHM user's manual (CHM viewer in synaptic). Take your time, and set it up just as it tells you to. It comes with a ISO image which your XP guest can mount and install drivers and software that make it blend more seamlessly with the ubuntu host. Once properly installed the OS's can share directories, the clipboard(though I've had some problems getting this to work), a mouse that is not imprisoned, and better USB support. USB support does require an entry in etc/Fstab- read the manual. My XP virtual machine is now a really useful tool that makes booting into my windows partition very rare indeed.-P.W.

---

