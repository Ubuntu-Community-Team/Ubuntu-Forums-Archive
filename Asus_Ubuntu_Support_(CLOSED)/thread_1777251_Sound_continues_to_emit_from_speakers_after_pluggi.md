---
title: "Sound continues to emit from speakers after plugging in headphones"
date: 2011-06-07
forum: Asus Ubuntu Support (CLOSED)
---

### Post by razzihaider on 2011-06-07
I have a problem, when i plug in headphone jack in to my laptop, i stll heard from both laptop speakers and the headphones, i have tried to fix this through editin .conf file, but it didn't worked. help me solve this. plz

---

### Post by CeeCeez on 2011-06-09
I have the same problem.  What model do you have?  Mine is K52J.

---

### Post by CeeCeez on 2011-06-09
Try this, worked for me!:D

[http://girliemangalo.wordpress.com/2011/04/15/fix-asus-k52j-speaker-sounds-with-ubuntu-10-10/](http://girliemangalo.wordpress.com/2011/04/15/fix-asus-k52j-speaker-sounds-with-ubuntu-10-10/)

---

### Post by fi2 on 2011-06-11
Eee: I have it the other way round. Inserting the jack the speaker goes mute, but the headphone does not sound up. It does with Win7.

What you say means that it does not alternate the outputs with the jack-switch, but uses separate amplifiers instead. Is it so?

I have't tried the solution above yet - I certainly will.

---

### Post by Vinton90 on 2011-06-13
I have the same problem. But I'm new at all this. I have an Asus U50F. However, when I tried the above fix it came back looking like this.

```

```wesley@wesley-laptop:~$ sudo apt-get install linux-alsa-driver-modules-$(wesley-r)
wesley-r: command not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-alsa-driver-modules
wesley@wesley-laptop:~$ sudo apt-get install linux-alsa-driver-modules
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-alsa-driver-modules
wesley@wesley-laptop:~$ 
```

```

I'm still searching around and I won't give up until I get it fixed but any help would be appreciated.
Thanks.

---

### Post by lidex on 2011-06-18
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by CloudShadow on 2011-06-19
I have the exact same problem, i entered the above command in terminal and this is what the end result says

grep: /tmp/alsa-info.NAKGoGVueu/wget.tmp: No such file or directory
Your ALSA information is located at 
Please inform the person helping you.

Any help would be very appreciated, i just switched from win 7 today and faced this problem. :(

---

### Post by batman408 on 2011-08-20
@Lidex

I have the same issue. 

Here's the link to my ALSA report - [http://www.alsa-project.org/db/?f=4a6d3dc61a35b4b5106a9c9e9de728f5321c51af]("http://www.alsa-project.org/db/?f=4a6d3dc61a35b4b5106a9c9e9de728f5321c51af")

I'd really appreciate if you could help, Thank You

---

### Post by lidex on 2011-08-22
> **batman408 said:**
> @Lidex

I have the same issue. 

Here's the link to my ALSA report - [http://www.alsa-project.org/db/?f=4a6d3dc61a35b4b5106a9c9e9de728f5321c51af]("http://www.alsa-project.org/db/?f=4a6d3dc61a35b4b5106a9c9e9de728f5321c51af")

I'd really appreciate if you could help, Thank You


Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by Linuxisfast on 2011-08-22
On my 1015B, all I have to do is plug in and reboot and it works.

---

### Post by batman408 on 2011-08-23
> **lidex said:**
> Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**
Hi Lidex,

I tried running the line of code in terminal and rebooting yet the problem is still the same. Sound only comes from headphones when connector is set to analog output, and even then the sound comes from both the headphones and the internal speakers. When switching the connector to Analog Headphones, nothing happens.

---

### Post by lidex on 2011-08-24
> **batman408 said:**
> Hi Lidex,

I tried running the line of code in terminal and rebooting yet the problem is still the same. Sound only comes from headphones when connector is set to analog output, and even then the sound comes from both the headphones and the internal speakers. When switching the connector to Analog Headphones, nothing happens.

Have a look here:
[http://ubuntuforums.org/showthread.php?t=1762969&highlight=headphones+asus+k60i](http://ubuntuforums.org/showthread.php?t=1762969&highlight=headphones+asus+k60i)

---

### Post by batman408 on 2011-08-24
> **lidex said:**
> Have a look here:
[http://ubuntuforums.org/showthread.php?t=1762969&highlight=headphones+asus+k60i](http://ubuntuforums.org/showthread.php?t=1762969&highlight=headphones+asus+k60i)
Perfect man, Thank yoU!

---

