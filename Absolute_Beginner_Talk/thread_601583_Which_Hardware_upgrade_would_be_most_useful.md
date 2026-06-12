---
title: "Which Hardware upgrade would be most useful?"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-11-03
I am running the computer in my sig.

I am transferring files from an external hard drive to my computer and it is slowing the whole system. In fact, this feels about twice as slow as Debian Etch. I really like Ubuntu though. I have decided to make an upgrade.

Should I upgrade my processor or my ram? 
If I upgrade my ram it will be to 2 gigs.
If I upgrade my processor I want it to be good. 

I don't know much about processors, so If I go that route I want some recommendations. I think I will eventually upgrade both, but I need something soon.

---

### Post by m9ke on 2007-11-03
If your system only slows down while transferring files from an external drive, there is a bottleneck somewhere between the external drive and where ever you are copying them to.  

What is the interface between the external drive and your system?  USB? some other?

---

### Post by tdrusk on 2007-11-03
it's usb.

The system feels slower even when I'm not transferring files. 

Example: 
To Open firefox in debian: 1 second
To Open firefox in Ubuntu: 3 seconds

---

### Post by m9ke on 2007-11-03
Let's see if we can isolate the problem.  You said
> Example:
To Open firefox in debian: 1 second
To Open firefox in Ubuntu: 3 seconds

Are you opening the app on the same computer?  

I see you are running Gutsy.  Did you have Fiesty before?  If so did your performance get worse when you upgraded?

Also using Firefox as a benchmark to compare the two OS'es might be tricky because a slow network connection might appear to slow down apparent opening time of the app.  Is there any task you could use to compare performance that has fewer variables?  Ie copying the same file to another dir under both OS'es,   Something like that.

Your original post asked what upgrade would be most useful.  Well, more RAM is always good, and a faster processor too.  But if one of these isn't the bottleneck hurting your performance, you will still end up wanting to figure that out after the upgrade.

---

### Post by jhenager on 2007-11-03
Celery Clock Speed  	1.20 to 2 GHz

I'd go with the RAM.

When you upgrade your CPU, make sure you get dual core. You'll thank yourself.

---

### Post by Duck2006 on 2007-11-03
> **jhenager said:**
> Celery Clock Speed  	1.20 to 2 GHz

I'd go with the RAM.

When you upgrade, make sure you get dual core. You'll thank yourself.

+1 on that one.

---

### Post by Fred_E _krugar on 2007-11-03
I suggest the ram and overclock the piss out of the processor
  
Of  course  you run the risk of burning the CPU but hey it was fun right? 

I have my X6700 running none stop at 3.5Ghz on Air and 3.9 ghz on my water settup.

---

### Post by vambo on 2007-11-03
IMO, Extra RAM is the best option for getting better performance

---

### Post by SOULRiDER on 2007-11-03
I think I would go for RAM too and maybe upgrade the processor once Core2 processors lower their prices.

---

### Post by tdrusk on 2007-11-03
Ram it is :)

Oh and to the person trying to isolate my problem... 

It got worse when I went from Feisty to Gutsy. I also turned off Desktop Effects in Gutsy to try to eliminate that problem.

To open a gnome terminal it takes longer in Gutsy than Debian Etch on the same computer.

---

### Post by joe.turion64x2 on 2007-11-04
In my experience Debian runs faster than any other 'comparable' distro (not talking about Puppy for example),  in fact I use it in my 'low specs' machines with excellent results. For example Debian Etch uses Gnome 2.14 while Ubuntu 7.10 uses Gnome 2.20 (?). It is just an 'older' array of software that accounts for a faster performance. So, your experience with both distros is completely normal.

Talking about the bottleneck you have, how fast is your HDD? I mean, is it a 4200RPM, or a 5400RPM one? That could be directly responsible for the slow data transfer rates. It it is a 4200RPM you'd better upgrade it to a 5400RPM one...it is worth the change.

I am not sure if your machine would support a dual core processor, you'd need to search in your manual/specs to find out, but of course adding RAM is the easiest way to boost performance. 

Finally take in mind that USB transfers are only fast in USB 2.0 ports (not 1.1), your external HD is USB, isn't it?

Joe.

---

### Post by joe.turion64x2 on 2007-11-04
This is your lappy [http://tienda.ndd.com.mx/acer-aspire-36802367-celeron-16ghz-512mb80gbdvdrwvista-home-p-2027.html](http://tienda.ndd.com.mx/acer-aspire-36802367-celeron-16ghz-512mb80gbdvdrwvista-home-p-2027.html) isn't it? If it has a SATA HDD then it shouldn't be the problem, provided the partition where Ubuntu is large enough/has at least 5% free space.

---

### Post by poision_heart on 2007-11-04
Hi buddy your lappy supports 2GB RAM so you should go with that.Yes upgrading processor is good idea but try with ram 1st.You harddisk is sata which is perfect one.I ll say about slow rate its matter of application ie old and new.I had same bad exp in feisty but gutsy is fast on my laptop.:)

---

### Post by joe.turion64x2 on 2007-11-04
Do you dualboot with Windows? If so then you can run the cpuz applet [http://www.cpuid.com/cpuz.php](http://www.cpuid.com/cpuz.php) and tell us a bit more about your processor, in case you still want to replace it.

---

### Post by joe.turion64x2 on 2007-11-04
> **joe.turion64x2 said:**
> Do you dualboot with Windows? If so then you can run the cpuz applet [http://www.cpuid.com/cpuz.php](http://www.cpuid.com/cpuz.php) and tell us a bit more about your processor, in case you still want to replace it.
Never mind. According to wikipedia, since your processor is a stripped down Core 2 Duo, it should be upgradeable to one of them.

---

