---
title: "iMac CPU Temperature readings....too high???"
date: 2011-06-18
forum: Apple Hardware Users
---

### Post by ishueli on 2011-06-18
Hi there,

I installed P sensor on my iMac to check the temperature sensor. I get following readings - 

CPU Diode    129C
CPU Proximity 129C
GPU 2 Diode 129C

Rest of the temperature readings are between 40-48 degC

Is this Ok? Please advise....

---

### Post by handy on 2011-06-18
On my 2007 model alu' 24" iMac:

CPU & Cache: 
Processor 0: Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz 2393MHz, 4096 KB Cache
Processor 1: Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz 2393MHz, 4096 KB Cache

My CPU temps are usually around 40 degrees C.

Following is the normal output that I get when I check using lm-sensors (I always like to see that my fans are running at minimum speed & the temperatures are nice): 

> radeon-pci-0100
Adapter: PCI adapter
temp1:        +31.0°C  

applesmc-isa-0300
Adapter: ISA adapter
ODD :         699 RPM  (min =  700 RPM)
HDD :        1199 RPM  (min = 1200 RPM)
CPU :        1199 RPM  (min = 1200 RPM)
TA0P:         +24.0°C  
TC0D:        +129.0°C  
TC0H:         +40.0°C  
TC0P:        +129.0°C  
TG0D:         +58.2°C  
TG0H:         +53.8°C  
TG0P:         +55.0°C  
TG1D:        +129.0°C  
TH0P:         +49.8°C  
TL0P:         +47.5°C  
TO0P:         +42.2°C  
TW0P:         +45.0°C  
Tm0P:         +46.0°C  
Tp0P:         +62.8°C  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +42.0°C  (high = +100.0°C, crit = +100.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:       +40.0°C  (high = +100.0°C, crit = +100.0°C)

---

### Post by ishueli on 2011-06-18
Many thanks Sir,

I am feeling kind of relieved to see the values that you have posted. I had a feeling that I was going to blow up my PC by installing LINUX..Here are the values that I see for the sensor...

DD :         1001 RPM
HDD :        1206
CPU :        1199
TA0P:         +25.8°C  
TC0D:        +129.0°C  
TC0H:         +42.2°C  
TC0P:        +129.0°C  
TG0D:         +60.5°C  
TG0H:         +57.8°C  
TG0P:         +58.0°C  
TG1D:        +129.0°C  
TH0P:         +48.0°C  
TL0P:         +44.5°C  
TO0P:         +43.0°C  
[COLOR=Red]**TW0P:         +66.5°C  **[/COLOR]
Tm0P:         +45.8°C  
Tp0P:         +70.8°C  

Tmp 1 is 34°C

I am using the screen widget to see the temperature values. How do you get to see the core values? Normally when I am running OSX, the core values are 37°C for both cores while with windows 7 it is 39°C.
I am still worried about TW0P temperature values. Any ideas how to control it?

Regards

---

### Post by handy on 2011-06-18
I occasionally have a look via lm-sensors.

If things were truly getting hot in there you would notice the fans becoming louder. I have never heard the fans do that since I bought this thing in 2007.

I wouldn't worry about the TWOP sensor's readout. I think you will find that the readings you get will vary very little as you watch it in the future. I know mine don't. 

I just get relatively minor variations in the CPU readings depending on how hard I'm working it, & such variations are what you would expect.

I think you should just observe the temperatures from time to time over the coming week or so, so that you gain confidence that everything is running just how it is supposed to. :)

---

### Post by alexmurray on 2011-06-19
The values of 129 seem like an integer conversion bug in the driver - the fact that they are always 129 and never change (and that 129 is 10000001 in binary sounds like its something wrong in reading the raw value and converting it to a real number) so I wouldn't be concerned - I doubt these are real readings, most likely as I said before a bug in the driver.

---

### Post by handy on 2011-06-19
I agree.

The power management that has been incorporated into the Linux systems in recent times does not allow me to control my iMac, via choosing a protocol for it to use.

That said, my observations through various tools indicate that the iMac is taking care of itself in a hardware based fashion that is at least partly beyond the control of the operating system, & doing a very good job of it too. :)

---

### Post by ishueli on 2011-06-20
Thanks again. Yes, I will be monitoring the temperature. 
 
Unity seems to be working fine on iMac now. However I am not able to use the magic mouse which I use often when I am working on OSX & Windows 7. However if I want to use Ubuntu 11.04, I have to connect a wired mouse. I tried to connect the mouse in various ways (reset bluetooth etc) and did manage to do so as well. But the mouse would then not work on OSX & Windows 7. I have to do pairing again to get it going on OSX. Is anyone of you using Magic mouse with Ubuntu 11.04? Does the connection stays ON after the reboot?

---

### Post by holastickboy on 2011-06-23
My iMac core i5 gets to about 59 degrees under load, and about 38 degrees at idle.  I agree with the other posters talking about the 129 degrees being a bug, as Intel says that the maximum tolerated heat by a core i15 is 120 degrees, so i would assume it would be already fried by now?  

Would it be wrong to assume that an iMac would shut down automatically as a hardware thing, regardless of the operating system, in a situation where it was overheating?

---

### Post by ishueli on 2011-06-23
I would assume that iMac will protect itself against overheating and will shut down on its own. Not experienced that as yet. The system seems to work good. 
 
By the I am still looking for a solution to the bluetooth problem. Do you use Magicmouse with your iMac? If yes then does it work in unity?

---

### Post by handy on 2011-06-23
No on the magicmouse. As far as I'm concerned it is the worst mouse that I have ever used in over 25 years of computing. (There is no accounting for taste I know. :))

I use a USB wired MS IntelliMouse Explorer 3.0, as it is a large mouse that suits my large hand & from past experience they last for about a decade of constant day to day use before dying. 

I don't like MS, but credit where credit is due.

---

### Post by holastickboy on 2011-06-23
I dual wield mouses, the magic mouse for when I'm doing productivity tasks, and a Razr mouse for everything else

---

