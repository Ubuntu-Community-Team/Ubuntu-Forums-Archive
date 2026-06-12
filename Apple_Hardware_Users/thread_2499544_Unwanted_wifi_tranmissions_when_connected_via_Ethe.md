---
title: "Unwanted wifi tranmissions when connected via Ethernet and during USB Boot"
date: 2024-07-30
forum: Apple Hardware Users
---

### Post by kixly on 2024-07-30
Hello Everyone,

I have been an Apple user and finally decided to switch over to Linux due to privacy concerns. 

I have spent the last 3 days trying different distros (Pop!_OS, Ubuntu, Fedora, elementary OS, Mint, Manjaro, openSUSE, Lubuntu, Cubes, and I attempted Debian but got hung up on the installation).
  
I only use Ethernet to connect to the internet, never Wifi or any wireless. This is for health reasons. 

I am using a 2013 Macbook Air.

I have 2 problems. 

1) Every time I boot up to a USB drive while holding down the option key while starting up there is a strong radio frequency spike that is transmitted at startup. I have a radio frequency meter and have noticed that this happens every time. I do not want my computer to do this. I talked to a tech friend awhile back and he said that it is probably something to do with the BIOS. Any ideas on how to adjust the BIOS settings?

2) This is the much bigger problem and it was a universal issue regardless of which Linux OS that I had tried from the above list. Whenever I would plug in my tp-link Ethernet-to-USB-adapter, there would be a steady Wifi pulsing. I shut off bluetooth and checked that the computer was configured to connect to the internet via Ethernet with every single operating system that I tried. While using Mint, I was able to unplug and replug in the adapter a few times to get the wifi transmission to stop.  But now I can´t seem to get that to work. I tried all three flavors of Mint (Cinnamon, MATE, xfce) and it no longer works to unplug and plug in the adapter in order to stop the wifi transmissions.

Ubuntu is one of my top choices for an OS but I will have to get another computer if I can´t figure out how to turn off the low power wifi pulsations. I was thinking that this might be a BIOS issue too. 

Any ideas on what I need to do to disable all wireless functionality on my laptop?

---

### Post by currentshaft on 2024-07-30
Why not just open the case and disconnect power to the wireless card?

---

### Post by kixly on 2024-07-30
UPDATE
I used this tutorial to remove the Wifi card                          [https://www.ifixit.com/Guide/MacBook+Air+13-Inch+Mid+2013+AirPort-Bluetooth+Card+Replacement/15179](https://www.ifixit.com/Guide/MacBook+Air+13-Inch+Mid+2013+AirPort-Bluetooth+Card+Replacement/15179)


That solved the Booting issue. 


But the second problem remains. I am still getting the radio frequency pulsing when the Ethernet adapter is plugged in.

---

### Post by currentshaft on 2024-07-30
Can you share your measurements? Are you certain it's the adapter that's emitting EMF and not the laptop itself?

---

### Post by kixly on 2024-07-31
When I remove the adapter it stops. When I plug the adapter back in, it starts again.

When  I remove the Ethernet cable, it continues pulsing (until I remove the adapter). So the meter is not  detecting frequencies traveling along the cable from the router. The  cable is a shielded Ethernet cable.   

I frequently check the  status of microwave transmissions at my computer set up and this is a  new phenomenon, specifically related to how the computer operates while  running the linux operating systems that I have tried. 

I could  try to get the power density measurement in micro-watts per meter  squared but this will vary depending on the distance from the adapter.  The point source for the  transmission is the adapter. The power density measurement drops off  fairly quickly as I pull the meter away from the adapter. The main thing  to say is that the pulse is relatively low powered (compared to a  standard wifi transmission from a laptop).  The meter detects the  frequency range from 650 MHz to 12 GHz.

The pulsing has the sound  signature of wifi (a steady machine gun type pulse). As opposed to the  higher pitch screeching from Bluetooth.

Because the power level of the pulsing is much lower than  typical wifi,  it is likely a form of electromagnetic interference (EMI)  generated through some interaction between the adapter and computer.


 The frequencies probably range from kilohertz pushing up  into the radio frequency (wireless) range. Thus moving through the air and being detected by the meter. 

This model of laptop does not have a built in Ethernet port and so I have to use a USB adapter.
 The brand on the adapter is TP Link.

 
The radio frequency meter that I have is accurate and sensitive.

 
A few times I was able to unplug the adapter, then  plug it back in and use the internet without the unwanted transmissions  but I have not been able to do that again for awhile. And of course I do  not want to have to fiddle with the connection every time I power up my  computer.

---

### Post by TheFu on 2024-07-31
I'd try a different USB-to-Ethernet adapter, if I was unwilling to shield myself from the cheap one I'm using.  In general, I'd avoid Chinese-made network equipment, but different people have different tolerances for that.

Is the TP Link device exceeding govt standards for RF leakage?  If so, contact your govt to complain.  They might do something, eventually. It won't help today, but in a year, perhaps all the TP Link devices will be better shielded from RF leaks?  If nobody complains, nothing will be done.

---

### Post by currentshaft on 2024-07-31
Time to test another adapter, another computer, another Ethernet cable, etc. until you rule out the issue, if it's important to you. However, billions of people use WiFi daily and don't think will generally empathize with your unqualified quest to dominate local airwaves.

---

### Post by kixly on 2024-07-31
I tried a different USB adapter. Problem solved.

---

### Post by kixly on 2024-07-31
Many people make all kinds of decisions that are harmful to themselves or the environment that they depend on. 
Just because many people share the same habit, it does not mean that the particular behavior is wise or healthy.
Thank you for the ideas and assistance. I have a workable solution now.  :P

---

### Post by kixly on 2024-07-31
Cheers **currentshaft** and **TheFu**.

---

