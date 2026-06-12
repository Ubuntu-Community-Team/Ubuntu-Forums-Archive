---
title: "GRUB question"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by super.rad on 2007-03-20
Just a quick question, if i install ubuntu on a 2nd hard drive will GRUB still install normally and give me the option which to boot into when starting the pc? Thanks

---

### Post by dbbolton on 2007-03-20
i really don't know about that. two partitions, sure. but i remember one fellow who couldn't get grub to recognise his second hard drive. i don't remember whether there was a solution to his problem or not. i'll have to root aroud and see if i can find that thread.

---

### Post by chaplanger on 2007-03-20
> **super.rad said:**
> Just a quick question, if i install ubuntu on a 2nd hard drive will GRUB still install normally and give me the option which to boot into when starting the pc? Thanks

This is the set up that I have.  WIN XP is on one hard drive and Ubuntu on my second hard drive.  GRUB is automatically installed in the Master Boot Record of the first hard drive and allows you to boot into either operating system (as long as both hard drives are running when you set up UBUNTU).  

The only thing to keep in mind is that UBUNTU sets itself up in GRUB as the first choice to automatically boot into.  If you want to change this after set-up the process is fairly simple and straight forward.

Hope this helps.

---

### Post by super.rad on 2007-03-20
brilliant thats all i wanted to know thanks, an not a problem about ubuntu putting itself first, once i've got it up and running with wireless aswell i wont be using xp unless i need to use a specific program

---

### Post by super.rad on 2007-03-20
Sorry if this is a stupid question, but if you dont ask you'll never know. Anyway i was wondering is it possible to install ubuntu through windows? doubt it is but thought it was worth asking

---

### Post by confused57 on 2007-03-20
> **super.rad said:**
> Sorry if this is a stupid question, but if you dont ask you'll never know. Anyway i was wondering is it possible to install ubuntu through windows? doubt it is but thought it was worth asking
You might be thinking about VMWare, which I'm not familiar with.

If you don't want grub installed to your Window's drive mbr, then you might want to read over this thread:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

If you don't want to disconnect your Windows drive to install Ubuntu, you could probably set your drive that you're installing Ubuntu on to boot before your Windows drive in bios, before you actually bootup the cd to install.  This way the installer "should" automatically add an entry to grub to boot Windows...your Window's drive mbr should be unaffected, which would allow you to boot your Window's drive(not using grub) by changing your bios hard drive boot order.

---

### Post by rusty4r on 2007-03-20
try taking a look at the grub page
[http://users.bigpond.net.au/hermanzone/p15.htm]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

