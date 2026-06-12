---
title: "Using graphics card in ubuntu VM on mac"
date: 2012-02-23
forum: Apple Hardware Users
---

### Post by verdagon on 2012-02-23
Hi everyone, quick question, I have installed ubuntu (oneiric, i think) on a vm on my new macbook pro (bought a week or so ago).

Is there any way I can get it to work with my mac's graphics card. It would help my development project.

Thanks!

- Evan

---

### Post by Haventfoundme on 2012-02-29
What are you using to Virtualize the Ubuntu guest? Have you installed the guest additions for that VM application to the guest OS? 

> 
VirtualBox Documentation
[[COLOR="YellowGreen"][COLOR="SeaGreen"]*Enable 3D acceleration*[/COLOR][/COLOR]]("http://www.virtualbox.org/manual/ch03.html#generalsettings")

    If a virtual machine has Guest Additions installed, you can select here whether the guest should support accelerated 3D graphics. Please refer to the section called “Hardware 3D acceleration (OpenGL and Direct3D 8/9)” for details.


---

