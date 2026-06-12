---
title: "[SOLVED] CPU temp"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by Johnny3 on 2007-12-05
When I type in sensors I get this
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +23°C
Core1 Temp:
             +27°C
Is this and ok temperature. Do I need to and them together to get true temperature.
23 + 27 = 50c
Thanks Johnny3
Gainesville Fl

---

### Post by anaconda on 2007-12-05
No, you dont add them together. I think it is the temperature from 2 separate points on your CPU..

The values sound OK to me..
Here are mine for comparison.

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
 +38°C
Core1 Temp:
 +39°C

---

### Post by PmDematagoda on 2007-12-05
Whoaaa, I never knew anyone could get a temperature lower than 30C on their PC as mine states 59C Processor Temperature.

So considering everything, your PC is much much better than mine when it comes to the amount of heat they produce, damn the Prescotts;).

---

### Post by meindian523 on 2007-12-05
same here...mine is 59 degrees at bootup in the BIOS......

@PMD

Actually,that's damaging our processors long term......aren't 2 fans enough??...1 SMPS and 1 independent....
You said Prescotts...meaning you have a Pentium D,correct?Do they have sensors??I don't know,just a question coz I installed the sensors package(tutorial from ubuntuguide.org) but when I gave the command for finding the temperature and other stuff,there was no output....???

---

### Post by Johnny3 on 2007-12-05
Thanks.
I have a Athlon 64x2 4600(65) windson. Have 1 1200 fan blowing in over hard drive in front, 1 1200 fan going out the back, on the side I have a 1200 blowing at video card and 80 blowing at the after mart CPU heat sink. Plus it is winter in Florida so room temp is 75 F. I like to keep things as cool as I can hope it will make PC last longer. I hope they don't change Ubuntu to much works great the way it is. Starting to like it a lot more than windows. I am 60++ in years so it takes me long to lean new things now. The only help I have is this Forum I would be lost with out it.
Thanks Johnny3
Gainesville Fl

---

### Post by PmDematagoda on 2007-12-05
> **meindian523 said:**
> same here...mine is 59 degrees at bootup in the BIOS......

@PMD

Actually,that's damaging our processors long term......aren't 2 fans enough??...1 SMPS and 1 independent....
You said Prescotts...meaning you have a Pentium D,correct?Do they have sensors??I don't know,just a question coz I installed the sensors package(tutorial from ubuntuguide.org) but when I gave the command for finding the temperature and other stuff,there was no output....???

Yes, they are damaging in the long term, but seems amazing to me since my processor is one year old and has been working at an average of about 59C all that time:-k.

It is not Pentium D, but is Pentium 4 HT.  And there are sensors, even though I couldn't get them fixed in 7.04, I did manage to do so in Ubuntu 7.10, so now I know what temperature my PC is in:).

---

### Post by drs305 on 2007-12-05
Johnny3,

Those temps are in the normal range but the sensors command can give inaccurate data. One way to check is to get into your systems BIOS during startup. You have to hit a key during the boot process - on my ASUS motherboard it's the DEL key. Many BIOS setups have utilities to check the temps of the CPU, motherboard, fan speeds, etc. 

If you find there are significant differences between the BIOS numbers (which should be more accurate) and the sensors data, you can make formula adjustments in the /etc/sensors.conf file (sensors3.conf file if you are using lm-sensors 3.0). That may sound easier than it actually is, but if you want to tackle it you can search the forum on how to do it.

---

### Post by meindian523 on 2007-12-06
> **PmDematagoda said:**
> Yes, they are damaging in the long term, but seems amazing to me since my processor is one year old and has been working at an average of about 59C all that time:-k.

It is not Pentium D, but is Pentium 4 HT.  And there are sensors, even though I couldn't get them fixed in 7.04, I did manage to do so in Ubuntu 7.10, so now I know what temperature my PC is in:).

hmm,no wonder...I'm using Feisty.....might have to try Gutsy just for this..... :)

---

### Post by oldb0y on 2007-12-06
There will almost always be a little difference between the BIOS-temp, and the temp registered when running an OS. Because the is more load on the CPU then.

---

