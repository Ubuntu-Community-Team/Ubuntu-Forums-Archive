---
title: "CPU is not scaled down anymore and ..."
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by taekr on 2008-01-11
Hi, all 

From yesterday after using Ubuntu Gusty Gibbon for about a month, all of sudden CPU scaling is not working. I have CPU scaling frequency monitor and system monitor on the panel.. 

And the strange thing is that system monitor shows that 'Processor: 100% in use'. When I opened the system monitor and click on 'Processes', I don't see any active use of CPU except 'system montior'. Sometimes swiftfox uses about 30 ~ 40% CPU but it's not still 100%. This is the weird... Something is going on, I think. 

I think becasue of that, CPU scaling montior indicates that CPU is 100% in use. When click on the resource monitor in System monitor, the graph named CPU History shows that CPU is running at 100% all the time. I looked at the Network History, but not much activity. I have 2GB memory and only less 30 % of physical memory is being used. 

I didn't access to BIOS to change any settings.  All I did was that I had some security updates via Update Manager. and.. just regular computing .. web browser.. email.. etc..   I don't play games.. 

Does anyone has any idea what is going on???

It was just fine before..

---

### Post by dcstar on 2008-01-11
> **taekr said:**
> Hi, all 

From yesterday after using Ubuntu Gusty Gibbon for about a month, all of sudden CPU scaling is not working. I have CPU scaling frequency monitor and system monitor on the panel.. 

And the strange thing is that system monitor shows that 'Processor: 100% in use'. When I opened the system monitor and click on 'Processes', I don't see any active use of CPU except 'system montior'. Sometimes swiftfox uses about 30 ~ 40% CPU but it's not still 100%. This is the weird... Something is going on, I think. 
..........

Open a terminal and use the** top** command, it may show more info.

---

### Post by shae on 2008-01-12
What is the output of

```
lsmod | grep powernow
```

---

