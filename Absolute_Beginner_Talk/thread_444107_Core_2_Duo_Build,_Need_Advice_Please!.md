---
title: "Core 2 Duo Build, Need Advice Please!"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by mocha on 2007-05-15
Hi all,

I'd appreciate your advice on a new build I'm doing.

MB:  probably Asus P5B-E or something similar, P965 based chipsets
CPU:  Core 2 Duo E6600, plan on overclocking to at least 3 GHz
Memory:  Corsair Twin2x2048-6400C4
Graphics:  something nVidia based, latest gen
HD:  something SATA based, latest gen
CD/DVD:  NEC ND-3550A, 3 year old IDE drive

I've been reading other posts and the wiki and there seems to be mixed results with this type of setup.  There's a lot of discussion about 32 vs 64 bit kernels and so forth, and also I don't understand this issue people are talking about the JMicron IDE controller.

According to the "specifications" tab on the Newegg site,

[[COLOR="Blue"]http://www.newegg.com/product/product.asp?item=N82E16813131070[/COLOR]]("http://www.newegg.com/product/product.asp?item=N82E16813131070")

the P5B-E has a JMicron controller only for 2 of its SATA ports.  The other 6 are on the Southbridge.  What about the IDE/PATA controller?  Is that a JMicron as well?

What should I do?  Should I stick with the configuration above and load the 64 bit generic kernel?  Should I consider different parts?  I want the most out of this system.  Thanks for any comments or suggestions.

---

### Post by Kobalt on 2007-05-15
> **mocha said:**
> I want the most out of this system.
If so then you should install Ubuntu64...

---

### Post by meborc on 2007-05-15
i think the jmicron chip bug was fixed in kernel upgrades a while ago... i don't know excactly when, but i bought my e6600 core 2 duo in november and i remember i was very worried when doing my ubuntu install... but since it had 945 chipset, everything worked out fine... i'm no computer expert, but 945 was the way to escape the jmicron problem... but as i said, i am pretty sure it was fixed... search the lounchpad (bugtracker) to find an open bug on jmicron... if you don't, then you are probably safe...

now on the subject of 32 vs 64 bit... i miself am running 32 bit because there are a lot of programs which need manual configuration to get them working under 64 bit... java and flash are difficult to say the least (i have never got them working under 64bit)... it comes down to your computer usage... if you really need that small speed boost (which was so small in my case that i didn't even notice) then install 64bit... if you need easy to configure / easy to run setup - install 32bit

---

### Post by mocha on 2007-05-16
```
java and flash are difficult to say the least (i have never got them working under 64bit)
```

Umm, okay thanks for the tip..  I won't be installing the 64 bit version then!

I searched for jmicron in the bugs section and there is nothing.

One other question, do you run the generic kernel?  I read that is the only way to get SMP working.  Thanks.

---

### Post by meborc on 2007-05-16
the generic kernel is installed out of the box :) so you must not worry about it... and fyi - both of my cores are recognized and running fine... got them both showing up in the system monitor also...

---

### Post by mocha on 2007-05-17
> **meborc said:**
> the generic kernel is installed out of the box :) so you must not worry about it... and fyi - both of my cores are recognized and running fine... got them both showing up in the system monitor also...

That't awesome!  How is the E6600?  Did you overclock it?  I've been reading alot about these systems.  People are getting 3+ GHz overclocks on the C2D's with stock cooling.  Have you overclocked yours?  I'm upgrading from a Barton 2600 so I'm sure my socks are gonna get blown off!!  Any other suggestions for installing Feisty?  Thanks.

---

### Post by Najand on 2007-05-17
Feisty 32 bits works just fine with my Core Duo 2 with jmicron chip. As "meborc" said, it is fixed for kernel 2.6.18 or above. 
Check:
[http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.18](http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.18)

---

### Post by mocha on 2007-05-17
Hi Najand,

Thanks for the link.

---

### Post by mjbeam on 2007-05-17
I installed on a core 2 duo with an ASUS P5B motherboard and had grub errors with my IDE hard drive on boot after the install. I bought a SATA II and most things are working great now. My DVD burner works. Wide screen 22" monitor at 1680x1050. Nvidia graphics card. Wireless mouse. Wireless Linksys network card. My USB keyboard was giving me problems so I hooked up a ps2 that I had laying around. From what I've read I think my printer is a lost cause in Linux. It's a Brother DCP-1000.

I've been running 7.04 for about 2 weeks now and I'm pretty happy with it so far. Much faster than Windows. I'll probably keep Vista on my Gateway Tablet PC because it's for school and there are always some Windows apps that they want us to run.


-Mike

---

### Post by stadt on 2007-05-17
> **mjbeam said:**
>  From what I've read I think my printer is a lost cause in Linux. It's a Brother DCP-1000.

Look here [http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html)

Brother has Linux drivers for your printer

---

### Post by bwtranch on 2007-08-01
I wrote a tutorial about the driver for dcp 1000 just today. Joined this forum just so I could post it. They are moderating it and it isn't up yet, so I am going to repeat it here. Didn't show up in an earlier search.

So you want it to PRINT, huh? Well scanning is easy and I would refer you to other fine articles for that. After much searching and frustration, I found nothing that worked until now. The instructions they give you don't work. You know that or you wouldn't be here, right? This is actually easy if you know how.

Download both the lpr and cupswrapper packages. Install the lpr FIRST, this is very important. This will not fully install and you will get an error. We can ignore it for now. We will come back and fix it later. We will have to because it messed up dpkg. 

Now install the cupwrapper package. This should go off without a hitch. Use the deb installer or shell command 
sh /usr/local/Brother/cupswrapper/cupswrapperDCP1000-1.0.2 -i and you possibly could get another error, but ignore that, too.

Then, Copy the file "/usr/share/cups/model/brsdp1000_cups.ppd"
to the directory "/usr/share/ppd".

If you are using USB interface,
connect the device to the PC and turn the power on.

Access to the page "http://localhost:631"
and click on "Add Printer",
then install the driver following the instructions.

Print a test page. Every thing OK? Think we are done? No, like I said installing the lpr package messed up dpkg and we have to fix it. --force does not work. Run "sudo gedit /var/lib/dpkg/status". Find the log for Brother lpr and it should say that it halfway installed. Delete the entry and save.

You can now go to Synaptic or whatever you like and delete the partially installed package.

Test printer again and I wish you good luck!:)

---

