---
title: "How come linux autodetects hardware???"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by elijahclarity on 2006-04-21
How is it that linux distros mostly autodetect most of my
hardware without my having to install the drivers off the CDs??
Do they (linux distros) come with loads of drivers for loads of hardware
PREINSTALLED?

And suppose if one piece of my hardware is not detected, can I build
a driver for it myself? How? (ignoring the fact that there may be drivers
available for it online)

Thanks:)

---

### Post by tribaal on 2006-04-21
Well actually linux does "load drivers" for your hardware, but it's not done in the same way than windows.

For the most common hardware, the drivers are included in the kernel as modules, for example, so most USB will work out of the box. For networking and CDroms, linux commes with really generic drivers, that can pretty much handle any device: optical drives all operate pretty much the same way, from the system's point of view, and manufacturers have interest in making their stuff as compatible as possible with what already exists.

Of course, very recent or specific hardware will not yet work out of the box (wireless cards anyone?), and for theses you will have to load specific drivers, just like in windows. Actually, you might even use *windows drivers* for some devices :)

I'm not sure I'm being really clear... does that answer your quesiton at all?

- trib'

---

### Post by gr0kzer0 on 2006-04-21
Can you write your own drivers? Sure, if you know about programming/reverse engineering. Then you could contribute yr code to the community and we can all benefit from yr hacking.

---

### Post by tribaal on 2006-04-21
Well we all use drivers that were once coded by someone, so I guess the answer is yes :)

A quick google search returned [this]("http://www.samag.com/documents/s=1208/sam9701a/9701a.htm").
Might be a good place to start with if you're really interested.

Cheers

- trib'

---

### Post by dcstar on 2006-04-21
[QUOTE=elijahclarity]
.......
And suppose if one piece of my hardware is not detected, can I build
a driver for it myself? How? (ignoring the fact that there may be drivers
available for it online)
[/QUOTE]
Many drivers depend on the hardware manufacturer to either build a Linux driver themselves, or provide the (sometimes very) detailed information about the product to assist external parties in creating a driver.

This can be very problematic, with some manufacturers reluctant to provide any proprietary Intellectual Property information, and you can find many Linux drivers for certain hardware "crippled" by this lack of information.

Some driver projects have had thousands of hours of time put into them, and still they don't work as well as the Windows ones the manufacturer is compelled to create.

---

