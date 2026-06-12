---
title: "any application to show network usage graph in 7.04?"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-05-23
Hi
thank you for reading my post
is there any application or something in ubuntu 7.04 that can shows network interface usage?


thanks

---

### Post by ahaslam on 2007-05-23
I have conky set up tpo show up & down graphs.

---

### Post by aks44 on 2007-05-23
GKrells does that (amongst other things).

---

### Post by arbulus on 2007-05-23
Gkrellm is a good one.  It monitors CPU, memory, network, swap, and loads of other things.  You can find it under Add/Remove Programs, Synaptic Package Manager, or in your terminal just type:

```
sudo apt-get install gkrellm
```

---

### Post by legolas_w on 2007-05-23
Thank you for reply, can you please include installation procedure?

thanks

---

### Post by Inxsible on 2007-05-23
Ubuntu has some system monitoring tools built in if you want to use them. I do not know how deep you wanna go into the statistics.
 
But if you right click on the top or the bottom panel and then Select Add to Panel. It shows up a dialog box of a bunch of tools that you can add to the panels. Under System Tools, select System Monitor. This will add a small box which shows processor usage. 
 
Right click on it and then you can add additional monitors like memory, swap usage, network bandwidth , and even hard disk access and usage.
 
But if you want something fancy then you might look into installing widgets like aDesklets or gDesklets or screenlets. More often than not, these widgets have widgets for system monitoring.

---

### Post by eentonig on 2007-05-23
Actually, he just did. that littel box with text, is the command you need to install it.

> sudo apt-get install gkrellm

Just open a terminal 
> <alt><F2> and enter > gnome-terminal

Now you can enter the install command.

And for GUI

System\Administration\Synaptic Package Manager

hit the search button en enter "gkrellm", click on the box in front of the correct line (hint, it's called "gkrellm") en select "mark for installation". Now that that's done, press apply.

Cheers

---

