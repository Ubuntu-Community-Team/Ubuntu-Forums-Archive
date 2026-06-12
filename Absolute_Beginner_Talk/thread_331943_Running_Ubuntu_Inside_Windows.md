---
title: "Running Ubuntu Inside Windows"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by pmcastillo on 2007-01-05
How?

Is it VMWare Player? I tried it, but it ask some config files and I don't know what to put.

---

### Post by CroEragon on 2007-01-05
If you use VMWare player you need to download virtual machine file from internet. You cant install ubuntu inside player it is just player.
Beware virtual ubuntu file will be same as real one. About 600 mb
You can download it from [here]("http://www.justfuckinggoogleit.com")
[img]http://www.justfuckinggoogleit.com/bart.gif[/img]

---

### Post by pmcastillo on 2007-01-05
Ah ok... or is there any program in the world that could access my installed Ubuntu from Windows?

---

### Post by scheuri on 2007-01-05
> **pmcastillo said:**
> Ah ok... or is there any program in the world that could access my installed Ubuntu from Windows?

Taken you mean "my ubuntu I installed on the same computer (read same hardware) as I my Windows is running" then...NO...it is not possible.

Best bet for running a operating system within another one (in your case you said Windows) you can use a VMware product.
VMware Player needs a pre existent VMware-Disk (a file which is the virtual harddisk of that other operating system).
What you are seeking for is a Vmware product in which you may install Ubuntu yourself such as Vmware Server (which is free) or Vmware Workstation (which costs money).

Your dual boot (meaning you start your PC and you can choose which OS it is booting) can not access both operatin systems at once...

sorry there.
scheuri

---

### Post by Bachstelze on 2007-01-05
Not true, VMWare can use a physical disk too and thus boot another OS installed on the host. It's not recommended to do so though, unless you know exactly what you're doing.

---

### Post by ajgreeny on 2007-01-05
And depending on what you mean by:-

Ah ok... or is there any program in the world that could access my installed Ubuntu from Windows?

yes there are a few that let you view, but not actually use the programs.  Have a look at explorefs2 (do a google search, and:-

[http://www.fs-driver.org/](http://www.fs-driver.org/)

which is supposed to give read/write of your ubuntu files.  I've not used that so can't comment further, but I do use explorefs2 on the odd ocasion I need to boot windows.

---

### Post by pmcastillo on 2007-01-05
> **ajgreeny said:**
> And depending on what you mean by:-

Ah ok... or is there any program in the world that could access my installed Ubuntu from Windows?

yes there are a few that let you view, but not actually use the programs.  Have a look at explorefs2 (do a google search, and:-

[http://www.fs-driver.org/](http://www.fs-driver.org/)

which is supposed to give read/write of your ubuntu files.  I've not used that so can't comment further, but I do use explorefs2 on the odd ocasion I need to boot windows.

Wow! Thanks man! Now I could put and get files in and out from Ubuntu

Thanks man!

---

