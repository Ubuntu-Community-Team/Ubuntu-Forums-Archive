---
title: "How do I get to set the FAN SPEED so that it keeps the CPU cool"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by shuttleworthwannabe on 2007-11-22
I have done a search to help me get to set the fan speed so that my CPU runs cooler than it right now: it is constantly at 56'C and goes hotter at CPU fires up with stress (application like Firefox, PDF viewing etc make the CPU reach peak firing most of the time--fan comes on, but tempt do not ever go down to 46'C like in XP.

Is there an application that can allow me to set the fan speed (I do not mind if it blows continuosly as long as the tempt cpu runs cooler tahn 56"C for now.

Looking forward to an answer; note other post like this one also ended in cul-de-sac. Hope there is a real solution to this,

S

---

### Post by mellowd on 2007-11-22
what cpu/motherboard/bios do you have?

---

### Post by mellowd on 2007-11-22
Also, is your fan on 2 or 3 pin power?

---

### Post by shuttleworthwannabe on 2007-11-22
Hi there thanks for the response
CPU: is Pentium M 2.13Ghz centrino 533Mhz
Motherboard: not sure how to check this
Bios: also not sure how to check this
Pin power: not sure what you are talking about


hardware is a HP Compaq nw8240 [(quickspecs)]("http://h18000.www1.hp.com/products/quickspecs/12140_na/12140_na.HTML")
Thanks for the prompt response.

S

---

### Post by tyggna1 on 2007-11-22
I know this isn't what you're looking for--but it might fix your problem.

I had a processor that kept jumping above 70C, and I didn't like that at all.  A *fairly* easy hard-ware fix is to spend $3-12 and buy some thermal grease.  Just by putting that stuff on I dropped my CPU temperature by about 12 degrees.

Just by putting that grease between my processor and fan did a bunch, then I added some on my heat-sink as well and that dropped it by a little bit too.

---

### Post by shuttleworthwannabe on 2007-11-22
ASIDE: I have read about this in the OS X forums: does this not require me to open the machine up; that is a problem, I have never tried this anytime. Anyway, I will for a software solution.

---

### Post by Niedzwiedz on 2007-11-22
I not sure if the fan can be adjusted in the BIOS, but, you can look.
Most Compaq Computers I have worked with not have much of a CPU fan. It a small thing that spins is how I refer to it. You may try looking at a few on-line sources for something better.
Here just a few links to look, not say you have to buy here, just learn;
[http://www.directron.com/index.html](http://www.directron.com/index.html)
[http://www.zipzoomfly.com/jsp/Home.jsp](http://www.zipzoomfly.com/jsp/Home.jsp) *Free Shipping*
Another thing you may try is a "Fan Controller" but, it just another thing to put a drag on your Power Supply ( Which, if, Stock may not be over 400 W)  and may cost more than a good fan. Most fans I buy come with the Thermal Paste, so you may not need to buy it just because someone say you need it.
 I want to make clear, I not refer to the answer on Thermal Paste above, that a good answer, but, "IF" you were to buy a Fan it may come with Thermal Paste.  But, there are better pastes too.

First you unplug your computer, and then figure out how to remove the side panel (Usually on the left from front view). Lay the computer on the other side and have a good light to see. The processor is up toward the Power Supply (PS) and you will see the fan on top. Look before you leap! See where the fan wires go, they may be even further up by the PS. Normally Compaq just stick the fan with some cheap stuff and it will come off when you careful. Just do not force it. (Actually it may have already fallen off the CPU and just hanging). You can try new paste as mentioned above or a new fan.

---

### Post by Niedzwiedz on 2007-11-22
Dang, I just looked at the Quick Specs (Sorry :( ) This not easy to get into, but, it can be done, I see if I can find the Support on this and give you a link.

---

### Post by mahiyar on 2007-11-22
I'am no expert or  have even used a compaq laptop extensively however here are two links that might prove helpful [http://ubuntuforums.org/showthread.php?t=250368](http://ubuntuforums.org/showthread.php?t=250368) [http://www.thinkwiki.org/wiki/ACPI_fan_control_script](http://www.thinkwiki.org/wiki/ACPI_fan_control_script)

---

### Post by Niedzwiedz on 2007-11-22
The link is the different manuals; (I just hope it work for you)
[http://h20000.www2.hp.com/bizsupport/TechSupport/DocumentIndex.jsp?contentType=SupportManual&lang=en&cc=nl&docIndexId=64902&taskId=101&prodSeriesId=462857#3](http://h20000.www2.hp.com/bizsupport/TechSupport/DocumentIndex.jsp?contentType=SupportManual&lang=en&cc=nl&docIndexId=64902&taskId=101&prodSeriesId=462857#3)
 IF the first link not work, try this link and look down for "Manuals" and click;
[http://h20000.www2.hp.com/bizsupport/TechSupport/SupportResources.jsp?lang=en&cc=nl&prodSeriesId=462857](http://h20000.www2.hp.com/bizsupport/TechSupport/SupportResources.jsp?lang=en&cc=nl&prodSeriesId=462857)

The first Guide is "Service and maintenance information" and you click; "HP Compaq nc8230, nx8220 and nw8240 Notebook PC-Maintence and Service Guide"

                      Table 1-2
          Left-Side Components (Continued)
Item Component         
5    Vent              
Function               Enables airflow to cool internal
                       components.
                       Ä   To prevent overheating, do not
                           obstruct vents. Do not allow a hard
                           surface, such as a printer, or a soft
                           surface, such as pillows or thick rugs
                           or clothing, to block airflow.

 This next Guide is "Software Reference" click Hardware and Software Guide"
Page 2-16
On select notebook models, Windows XP supports software
that enables you to control processor performance. The central
processing unit (CPU) speed can be set for optimal performance
or for optimal power conservation.

These Guides may help you adjust the fan or clean a vent. IF, you need to get inside they tell how and show a break down to help give you a visual. Getting into a Laptop is not fun and it good to have your PDF file on another computer for reference.

---

### Post by pdlethbridge on 2007-11-22
windows had an app that could solve the problem. It's call motherboard monitor. It has a range of motherboards that it covers and controls fan speeds for all fans in the computer. I don't know if it will work through wine, but you could give it a try. Motherboard Monitor [http://www.majorgeeks.com/download.php?det=311](http://www.majorgeeks.com/download.php?det=311)

---

### Post by JBAlaska on 2007-11-22
Just proping up your laptop like so; [[IMG]http://img222.imageshack.us/img222/2300/laptopcoolgp8.jpg[/IMG]](http://imageshack.us) can make a big difference on airflow.

Or you can get a active "Cool Pad" with fans in it to dissipate heat.
```
http://www.hardwarecooling.com/default.php/cat/33/Laptop_Cooling
```

---

