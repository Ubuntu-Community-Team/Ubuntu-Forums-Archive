---
title: "[RFC] Fan control for mactel-support repo"
date: 2010-04-30
forum: Apple Hardware Users
---

### Post by kosumi68 on 2010-04-30
One of the most long-lived discussions regarding running Ubuntu on Macs is the problem of excessive heat. There exist solutions for every single case, but they are somewhat hard for the newcomer to find.

This post is a request for a fan-control solution suitable for all macs, to eventually be put in the mactel-support repository. I know there are several fan-control solutions out there, and my hope is that this thread will single out one of them to improve upon to the point that everybody can install and use it on their mac.

So, do you have a solution? Please come forward :-)

---

### Post by xxander on 2010-04-30
I also need help with this.

---

### Post by alexmurray on 2010-05-01
A while ago I started work on a solution which composed a simple daemon to set the fan speeds, which exposed a dbus interface and allowed a client panel applet (or similar perhaps application indicator now with latest Ubuntu could be used) to monitor temps and set fan speed automatically (this would also provide a GUI to show the current temps, fan speeds etc and allow user control perhaps as well) - never finished it entirely but if people are keen I can try and finish it off / at least post the code if someone else wants to try and continue it.

---

### Post by kosumi68 on 2010-05-01
> **alexmurray said:**
> A while ago I started work on a solution which composed a simple daemon to set the fan speeds, which exposed a dbus interface and allowed a client panel applet (or similar perhaps application indicator now with latest Ubuntu could be used) to monitor temps and set fan speed automatically (this would also provide a GUI to show the current temps, fan speeds etc and allow user control perhaps as well) - never finished it entirely but if people are keen I can try and finish it off / at least post the code if someone else wants to try and continue it.

By all means! It is probably a good idea for the fan control core to work directly with the sysfs interface of the applesmc, in case people use different setups. Some people might even run without dbus, for all we know. But on top of that, graphical tools are of course great.

---

### Post by linuxopjemac on 2010-05-02
I also hope that you can continue this project. It makes running Ubuntu on an Intel Mac smoother.

---

### Post by hsoJoshFTW on 2010-05-02
I definitely need a fan controller for my MacBook also! It seems to be running really hot whenever I use Ubuntu 10.4. I need a way to increase the speeds of the fans or something to cool it down.

---

### Post by kosumi68 on 2010-05-04
Thanks to Alex Murray, we now have temperature labels in the applesmc sysfs interface, available via the mactel PPA. This is a big step towards realizing the one-model-fits-all fan control script. Kudos.

---

### Post by linuxopjemac on 2010-05-05
kudos and respect !

---

### Post by dngfng on 2010-08-23
Hi,
I was hopeing to find a solution hear to the heat/fan control problems for my MacBook Pro 6,2. But I fail to see a solution hear. 

Can someone point me in the right direction?

Thanks in advanced.

BTW - has anybody had a look at this solution:
[http://paste2.org/p/862259](http://paste2.org/p/862259)

or this one:
[http://ubuntuforums.org/showpost.php?p=9729383&postcount=57](http://ubuntuforums.org/showpost.php?p=9729383&postcount=57)

---

### Post by SwedishWings on 2010-08-24
I wrote a C daemon that does the job, at least for me on Lucid and MacBook Pro 5,1. Please try it out and give me feed back.

See the README file.

/Mike

---

### Post by ryanczak on 2010-08-24
I wrote a python daemon that works for me. I am using a 13 inch macbook pro 7,1 . 

This daemon only works with the 13 inch though because it expects only one fan to be present. I used to use it on a plain (non-pro) macbook 13 inch and it worked fine there. It is pretty self explanatory to tweak in regards to how sensitive it is to heat but if you have questions feel free to pm me. 

You find the script and some instructions here:

[http://planetfoo.org/blog/2009/11/13/macbook-fan-control-in-linux/](http://planetfoo.org/blog/2009/11/13/macbook-fan-control-in-linux/)

---

### Post by furok23 on 2010-08-24
> **SwedishWings said:**
> I wrote a C daemon that does the job, at least for me on Lucid and MacBook Pro 5,1. Please try it out and give me feed back.

See the README file.

/Mike

just installed on my MPB 6,2. ill be giving you a full professional review *sarcasm* on whatever comes of it. as of now, its working great. youda man

question: which temp output is it monitoring?

currently i have my system set to monitor the gpu, and TPCD (not sure what it is, but its hot lol)

---

### Post by dngfng on 2010-08-25
Just had a look at your code it looks pretty cool - will try it out later.

Even so using average temperature is probably not quite as effective as we should really monitor the sensors near the CPU and Graphics card. As those will give a better idea of the relevant temperatures. 

At least for MBP 6,2 it looks like the two to watch are temp7_input and temp11_input.

If we work together we may be able to figure out the relevant sensors for different MacBooks.

Also is there a particular reason why you set the min fan speed to 0 since OSX seems to keep both running at 2000 even when idle. 

[COLOR=Red]
[/COLOR]

---

### Post by SwedishWings on 2010-08-25
Thanks for trying it out =D

It takes average on all sensors it can find, hence the narrow span of temperatures set in /etc/macfanctl.conf. 

The idea to use all sensors come from from a fan control program i use on OSX, that is working great for me. Another advantage is that the program become quite generic and don't need specific configuration for different versions of MacBook. However, I'm happy to rewrite it to use specific sensors if it does not work properly for you.

The reason that i set min fan speed to 0 is that it really has no effect on operation when i tested it. Try it out. I think you reach the same conclusion.

And of course, feel free to mod the code, and send it back to me for merging if you want! This was a Q&D hack, so there is room for improvements =D

Cheers!

/Mike


EDIT: For reference, please compare your readings with mine below (macfanctl run with -d). Here the fan starts to run after 45 seconds (each line is 5 seconds). I live in a hot place, Philippines, and at the this time it's about 32C in my condo.

```
mike@mike-laptop:~$ head -n 30 /var/log/macfanctl.log 
Number of sensors found: 20
Parameters: temp_floor: 43, temp_ceiling: 48, fan_min: 0
Speed: 0, Avg temp: 40.1
Speed: 0, Avg temp: 40.3
Speed: 0, Avg temp: 40.7
Speed: 0, Avg temp: 41.0
Speed: 0, Avg temp: 41.5
Speed: 0, Avg temp: 41.8
Speed: 0, Avg temp: 42.2
Speed: 0, Avg temp: 42.5
Speed: 0, Avg temp: 42.9
Speed: 201, Avg temp: 43.2
Speed: 588, Avg temp: 43.5
Speed: 930, Avg temp: 43.8
Speed: 1581, Avg temp: 44.3
Speed: 1751, Avg temp: 44.4
Speed: 1751, Avg temp: 44.4
Speed: 1766, Avg temp: 44.4
Speed: 1953, Avg temp: 44.6
Speed: 2448, Avg temp: 45.0
Speed: 2046, Avg temp: 44.7
Speed: 2030, Avg temp: 44.6
Speed: 1937, Avg temp: 44.6
Speed: 1921, Avg temp: 44.5
Speed: 2014, Avg temp: 44.6
Speed: 2030, Avg temp: 44.6
Speed: 2076, Avg temp: 44.7
Speed: 2278, Avg temp: 44.8
Speed: 2231, Avg temp: 44.8
Speed: 2185, Avg temp: 44.8
```

---

### Post by dngfng on 2010-08-25
Cool - will try it out as it is.

As I said I do like the code.

I am just a tad worried that their may be some applications that are only CPU or GPU intensive thus one requiring more cooling then the other.

Will post my output once I get home and around to running the daemon.

---

### Post by SwedishWings on 2010-08-25
> **dngfng said:**
> I am just a tad worried that their may be some applications that are only CPU or GPU intensive thus one requiring more cooling then the other.

Good point to check this. I tried a full backup with tar and bzip2 compression. It took the daemon about 20 seconds to get the fan to full speed. I don't know of an GPU intensive app that don't load the CPU. Any suggestions?

---

### Post by dngfng on 2010-08-25
> **SwedishWings said:**
> Good point to check this. I tried a full backup with tar and bzip2 compression. It took the daemon about 20 seconds to get the fan to full speed. I don't know of an GPU intensive app that don't load the CPU. Any suggestions?

folding@home gpu verison - should proably do the trick. Also it may be intresting to get running log outputs (maybe in a differnt file) of the tempretures measured by the different sensors so we can spot the hotspots.

[http://www.overclock.net/overclock-net-folding-home-team/436453-linux-gpu2-folding.html](http://www.overclock.net/overclock-net-folding-home-team/436453-linux-gpu2-folding.html)

hmm - even so that only runs vie wine ...

---

### Post by SwedishWings on 2010-08-25
I found this in the [source of applesmc]("http://lxr.free-electrons.com/source/drivers/hwmon/applesmc.c"):

```
 86 static const char *temperature_sensors_sets[][41] = {
 87 /* Set 0: Macbook Pro */
 88         { "TA0P", "TB0T", "TC0D", "TC0P", "TG0H", "TG0P", "TG0T", "Th0H",
 89           "Th1H", "Tm0P", "Ts0P", "Ts1P", NULL },
 90 /* Set 1: Macbook2 set */
 91         { "TB0T", "TC0D", "TC0P", "TM0P", "TN0P", "TN1P", "TTF0", "Th0H",
 92           "Th0S", "Th1H", NULL },
 93 /* Set 2: Macbook set */
 94         { "TB0T", "TC0D", "TC0P", "TM0P", "TN0P", "TN1P", "Th0H", "Th0S",
 95           "Th1H", "Ts0P", NULL },
 96 /* Set 3: Macmini set */
 97         { "TC0D", "TC0P", NULL },
 98 /* Set 4: Mac Pro (2 x Quad-Core) */
 99         { "TA0P", "TCAG", "TCAH", "TCBG", "TCBH", "TC0C", "TC0D", "TC0P",
100           "TC1C", "TC1D", "TC2C", "TC2D", "TC3C", "TC3D", "THTG", "TH0P",
101           "TH1P", "TH2P", "TH3P", "TMAP", "TMAS", "TMBS", "TM0P", "TM0S",
102           "TM1P", "TM1S", "TM2P", "TM2S", "TM3S", "TM8P", "TM8S", "TM9P",
103           "TM9S", "TN0H", "TS0C", NULL },
104 /* Set 5: iMac */
105         { "TC0D", "TA0P", "TG0P", "TG0D", "TG0H", "TH0P", "Tm0P", "TO0P",
106           "Tp0C", NULL },
107 /* Set 6: Macbook3 set */
108         { "TB0T", "TC0D", "TC0P", "TM0P", "TN0P", "TTF0", "TW0P", "Th0H",
109           "Th0S", "Th1H", NULL },
110 /* Set 7: Macbook Air */
111         { "TB0T", "TB1S", "TB1T", "TB2S", "TB2T", "TC0D", "TC0P", "TCFP",
112           "TTF0", "TW0P", "Th0H", "Tp0P", "TpFP", "Ts0P", "Ts0S", NULL },
113 /* Set 8: Macbook Pro 4,1 (Penryn) */
114         { "TB0T", "TC0D", "TC0P", "TG0D", "TG0H", "TTF0", "TW0P", "Th0H",
115           "Th1H", "Th2H", "Tm0P", "Ts0P", NULL },
116 /* Set 9: Macbook Pro 3,1 (Santa Rosa) */
117         { "TALP", "TB0T", "TC0D", "TC0P", "TG0D", "TG0H", "TTF0", "TW0P",
118           "Th0H", "Th1H", "Th2H", "Tm0P", "Ts0P", NULL },
119 /* Set 10: iMac 5,1 */
120         { "TA0P", "TC0D", "TC0P", "TG0D", "TH0P", "TO0P", "Tm0P", NULL },
121 /* Set 11: Macbook 5,1 */
122         { "TB0T", "TB1T", "TB2T", "TB3T", "TC0D", "TC0P", "TN0D", "TN0P",
123           "TTF0", "Th0H", "Th1H", "ThFH", "Ts0P", "Ts0S", NULL },
124 /* Set 12: Macbook Pro 5,1 */
125         { "TB0T", "TB1T", "TB2T", "TB3T", "TC0D", "TC0F", "TC0P", "TG0D",
126           "TG0F", "TG0H", "TG0P", "TG0T", "TG1H", "TN0D", "TN0P", "TTF0",
127           "Th2H", "Tm0P", "Ts0P", "Ts0S", NULL },
128 /* Set 13: iMac 8,1 */
129         { "TA0P", "TC0D", "TC0H", "TC0P", "TG0D", "TG0H", "TG0P", "TH0P",
130           "TL0P", "TO0P", "TW0P", "Tm0P", "Tp0P", NULL },
131 /* Set 14: iMac 6,1 */
132         { "TA0P", "TC0D", "TC0H", "TC0P", "TG0D", "TG0H", "TG0P", "TH0P",
133           "TO0P", "Tp0P", NULL },
134 /* Set 15: MacBook Air 2,1 */
135         { "TB0T", "TB1S", "TB1T", "TB2S", "TB2T", "TC0D", "TN0D", "TTF0",
136           "TV0P", "TVFP", "TW0P", "Th0P", "Tp0P", "Tp1P", "TpFP", "Ts0P",
137           "Ts0S", NULL },
138 /* Set 16: Mac Pro 3,1 (2 x Quad-Core) */
139         { "TA0P", "TCAG", "TCAH", "TCBG", "TCBH", "TC0C", "TC0D", "TC0P",
140           "TC1C", "TC1D", "TC2C", "TC2D", "TC3C", "TC3D", "TH0P", "TH1P",
141           "TH2P", "TH3P", "TMAP", "TMAS", "TMBS", "TM0P", "TM0S", "TM1P",
142           "TM1S", "TM2P", "TM2S", "TM3S", "TM8P", "TM8S", "TM9P", "TM9S",
143           "TN0C", "TN0D", "TN0H", "TS0C", "Tp0C", "Tp1C", "Tv0S", "Tv1S",
144           NULL },
145 /* Set 17: iMac 9,1 */
146         { "TA0P", "TC0D", "TC0H", "TC0P", "TG0D", "TG0H", "TH0P", "TL0P",
147           "TN0D", "TN0H", "TN0P", "TO0P", "Tm0P", "Tp0P", NULL },
148 /* Set 18: MacBook Pro 2,2 */
149         { "TB0T", "TC0D", "TC0P", "TG0H", "TG0P", "TG0T", "TM0P", "TTF0",
150           "Th0H", "Th1H", "Tm0P", "Ts0P", NULL },
151 /* Set 19: Macbook Pro 5,3 */
152         { "TB0T", "TB1T", "TB2T", "TB3T", "TC0D", "TC0F", "TC0P", "TG0D",
153           "TG0F", "TG0H", "TG0P", "TG0T", "TN0D", "TN0P", "TTF0", "Th2H",
154           "Tm0P", "Ts0P", "Ts0S", NULL },
155 /* Set 20: MacBook Pro 5,4 */
156         { "TB0T", "TB1T", "TB2T", "TB3T", "TC0D", "TC0F", "TC0P", "TN0D",
157           "TN0P", "TTF0", "Th2H", "Ts0P", "Ts0S", NULL },
158 /* Set 21: MacBook Pro 6,2 */
159         { "TB0T", "TB1T", "TB2T", "TC0C", "TC0D", "TC0P", "TC1C", "TG0D",
160           "TG0P", "TG0T", "TMCD", "TP0P", "TPCD", "Th1H", "Th2H", "Tm0P",
161           "Ts0P", "Ts0S", NULL },
162 /* Set 22: MacBook Pro 7,1 */
163         { "TB0T", "TB1T", "TB2T", "TC0D", "TC0P", "TN0D", "TN0P", "TN0S",
164           "TN1D", "TN1F", "TN1G", "TN1S", "Th1H", "Ts0P", "Ts0S", NULL },
165 };

```

As the daemon reads the sensors names, it would be easy to pick out the applicable sensors and use them.

According [to the key names i found here]("http://www.parhelia.ch/blog/statics/k3_keys.html"):

```
 Bit   Hex      Dec    Key   Description
 ---  ------   -----   ----  ------------
  0   0x0001       1   TC0H  CPU Heatsink
  1   0x0002       2   TG0H  GPU Heatsink
  2   0x0004       4   TH0P  HDD Proximity
  3   0x0008       8   TO0P  ODD Proximity
  4   0x0010      16   Tm0P  MLB Proximity
  5   0x0020      32   TA0P  Ambient
  6   0x0040      64   Tp0P  Power Supply Proximity
  7   0x0080     128   TW0P  Wireless (Airport) Proximity
  8   0x0100     256   TC0P  CPU Proximity
  9   0x0200     512   TC0D  CPU Die
 10   0x0400    1024   TG0P  GPU Proximity
 11   0x0800    2048   TG0D  GPU Die
 12   0x1000    4096   TL0P  LCD Proximity
 13   0x2000    8192   SGTT  GPU Heatsink Throttle Threshold
```
 
The relevant sensors would be TC0P and TG0P, which indeed maps well to temp7_input and temp11_input, when i run 

```
mike@mike-laptop:~/scripts$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +50.0°C  (high = +105.0°C, crit = +105.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +50.0°C  (high = +105.0°C, crit = +105.0°C)  

applesmc-isa-0300
Adapter: ISA adapter
Left side  :4265 RPM  (min = 4262 RPM)
Right side :4253 RPM  (min = 4262 RPM)
TB0T:        +33.5°C                                    
TB1T:        +33.5°C                                    
TB2T:        +32.5°C                                    
TB3T:        +33.5°C                                    
TC0D:        +54.0°C                                    
TC0F:        +51.2°C                                    
TC0P:        +50.8°C   <=== temp7_input                                 
TG0D:        +61.0°C                                    
TG0F:        +56.2°C                                    
TG0H:        +45.2°C                                    
TG0P:        +56.0°C   <=== temp11_input                                 
TG0T:        +55.0°C                                    
TG1H:        +54.8°C                                    
TN0D:        +56.0°C                                    
TN0P:        +53.8°C                                    
TTF0:        +65.0°C                                    
Th2H:        +48.8°C                                    
Tm0P:        +54.5°C                                    
Ts0P:        +32.2°C                                    
Ts0S:        +42.8°C
```

I think i have enough information to use the relevant sensors. The idea would be to read the labels of the sensors and then use TC0P an TG0P. In  this way, the code would be location independent (i.e not use "temp7_input" or "temp11_input"). That would make it pretty generic i hope. As a fall back if the sensor names are not found, it could revert to current average algorithm.

However, please try it out first. If it works with the average, it feels like a more general solution.

/Mike

---

### Post by dngfng on 2010-08-25
Looks good to me - especially having the average as a fall back.

To make it more generic, you will also have to consider MacBooks with only one FAN

Great stuff

Also just had a quick look at applesmc - it looks like there is a big chunk of fan control stuff - wonder why it doesn't work/appears not to be working.

---

### Post by SwedishWings on 2010-08-25
After a bit more searching, i found this[ unofficial Apple document, "Apple Service Diagnostic Test Results Guide"]("http://herku.info/Apple/Mac%20Os%20X%20Software/new/ASD%203S132/ASD%20Test%20Results%20Guide.pdf")

All sensor names are defined. Quite valuable i think =D

---

### Post by dngfng on 2010-08-25
> **SwedishWings said:**
> After a bit more searching, i found this[ unofficial Apple document, "Apple Service Diagnostic Test Results Guide"]("http://herku.info/Apple/Mac%20Os%20X%20Software/new/ASD%203S132/ASD%20Test%20Results%20Guide.pdf")

All sensor names are defined. Quite valuable i think =D

Replace quite with very ;);)

Looks like you found what is need to take the proper readings.

Good stuff :D

---

### Post by SwedishWings on 2010-08-25
Ok, let's do this.

The primary mode will be to use TC0P and TG0P, average will be the fall back. 

What i need to know is what temperatures are good for floor and ceiling values. Any ideas?

---

### Post by dngfng on 2010-08-25
> 
To save battery on a laptop, I think that the fan should not come on  when the computer is doing anything less intensive than watching a  movie, so I set that fan to kick in at 65C.  This coincides with what  Mac OSX does.  From OSX, it appears that the fans should hit full speed  at 80C and the speed builds up exponentially to that point.  

The formula  I use for changing the fan speed when the temperature is increasing is:

temp <= 65:
   speed = max(current_speed, 2000)
65 < temp < 80:
   step = (6200 - 2000) / ( (80 - 65) * (80 - 64) / 2 )
   speed = max(current_speed, ceil(2000 + (temp - 65) * (temp - 64) / 2 * step))
temp >= 80:
   speed = 6200


[http://allanmcrae.com/2010/05/simple-macbook-pro-fan-daemon/](http://allanmcrae.com/2010/05/simple-macbook-pro-fan-daemon/)

According to this source OSX kicks in > 65 C and tops out at 80 C - obviously this is not a 100% accurate source.

---

### Post by SwedishWings on 2010-08-25
Ok, 

here is an update, with these changes:

* Defaults to use TC0D and TG0D (die temp). Note, that i did some logging and found that TC0D and TG0D reacts much faster to temp changes than TC0P and TG0P (proximity temp).
* Added a new switch "-a" that forces average mode.
* Added some more info on startup to the log file. It looks like this now:
```
Found 20 sensors:
	TB0T - Battery TS_MAX Temp
	TB1T - Battery TS1 Temp
	TB2T - Battery TS2 Temp
	TB3T - Battery Temp
	TC0D - CPU 0 Die Temp
	TC0F - ?
	TC0P - CPU 0 Proximity Temp
	TG0D - GPU Die - Digital
	TG0F - ?
	TG0H - Left Heat Pipe/Fin Stack Proximity Temp
	TG0P - GPU 0 Proximity Temp
	TG0T - GPU 0 Die - Analog Temp
	TG1H - Left Heat Pipe/Fin Stack Proximity Temp
	TN0D - MCP Die
	TN0P - MCP Proximity
	TTF0 - ?
	Th2H - Right Fin Stack Proximity Temp
	Tm0P - Battery Charger Proximity Temp
	Ts0P - ?
Using TC0D and TG0D for fan speed control.
Using parameters:
	temp_avg_floor: 43
	temp_avg_ceiling: 48
	temp_TC0D_floor: 55
	temp_TC0D_ceiling: 70
	temp_TG0D_floor: 65
	temp_TG0D_ceiling: 80
	fan_min: 0
Speed: 2480, *TC0D: 61.0C, TG0D: 67.0C
Speed: 2066, *TC0D: 60.0C, TG0D: 67.0C
Speed: 2066, *TC0D: 60.0C, TG0D: 66.0C
Speed: 2583, *TC0D: 61.2C, TG0D: 67.0C
Speed: 2170, *TC0D: 60.2C, TG0D: 67.0C
...

```
* Added new parameters in /etc/macfanctl.conf:
```
# Config file for macfanctl daemon
fan_min: 0

temp_avg_floor: 43
temp_avg_ceiling: 48

temp_TC0D_floor: 55
temp_TC0D_ceiling: 70

temp_TG0D_floor: 65
temp_TG0D_ceiling: 80

```

Try it out and see if it works!

/Mike

---

### Post by dngfng on 2010-08-26
Great work - sorry I wasn't able to try it out last night but will defiantly get around to installing it tonight after work.

You should really publish this as Beer-ware Licenses - if you are ever around in Cologne give me a shout so I can buy you a Mühlen Kölsch.

---

### Post by SwedishWings on 2010-08-26
> **dngfng said:**
> Great work - sorry I wasn't able to try it out last night but will defiantly get around to installing it tonight after work.

You should really publish this as Beer-ware Licenses - if you are ever around in Cologne give me a shout so I can buy you a Mühlen Kölsch.


Mühlen Kölsch? Thanks, have no idea what that is, though it sounds like beer, and if it is, i like it =D

I'm trying hard to get this into the ppa, but have failed so far. Meanwhile, i attach a deb package. Note that the doc's are not updated so Beer-ware ;) 

Cheers!

---

### Post by dngfng on 2010-08-27
The fan control seems to work pretty well so far. I have just noticed that there where certain spikes where the fan would spin up and suddenly spin down again.

Think it was something like a drop from 4000-5000RPM down to 2000RPM within 1 sensor read cycle - the temperatures had dropped to the proper level.

I will collect some logs to be able to identify these sudden drops in RPM.  

Maybe we can optimise the Fan speed as I am guessing it spun up higher then it would have needed to. 

Also there is the very likely case that I just found the sudden turn off odd. As it could very well be sensible to do so.

Mühlen Kölsch is beer -  [http://www.muehlenkoelsch.de/en/brewhouse.php](http://www.muehlenkoelsch.de/en/brewhouse.php)

Anyway thanks for the great Daemon

---

### Post by SwedishWings on 2010-08-27
Finally got it in the PPA!

To install macfanctld do:
```

$ sudo add-apt-repository ppa:mikael-sesamiq/ppa
$ sudo add-apt-get update
$ sudo add-apt-get install macfanctld

```

I hope this will work.

/Mike

---

### Post by dngfng on 2010-08-27
Cool - should make life easier for all future heat effected users

---

### Post by SwedishWings on 2010-08-27
> **dngfng said:**
> The fan control seems to work pretty well so far. I have just noticed that there where certain spikes where the fan would spin up and suddenly spin down again.

Think it was something like a drop from 4000-5000RPM down to 2000RPM within 1 sensor read cycle - the temperatures had dropped to the proper level.

I will collect some logs to be able to identify these sudden drops in RPM.  

Maybe we can optimise the Fan speed as I am guessing it spun up higher then it would have needed to. 

Also there is the very likely case that I just found the sudden turn off odd. As it could very well be sensible to do so.

Mühlen Kölsch is beer -  [http://www.muehlenkoelsch.de/en/brewhouse.php](http://www.muehlenkoelsch.de/en/brewhouse.php)

Anyway thanks for the great Daemon

I noticed the spikes too. It runs much smoother in the average (-a) mode. 

It might be as simple as classic overshoot due to hysteresis in the control loop temp/fan. The TC0D and TG0D sensors jump pretty quickly when the load changes and causes some over shoot. This is not the case in average mood as the average reacts much slower (smaller gradient).

I've been thinking about a third mode (... and one to rule them all...) where i use TC0D, TG0D and average, and any of them can drive the fan. This might not eliminate the over shoot, but would certainly give a very safe temperature control.

What do you think?

---

### Post by dngfng on 2010-08-27
> **SwedishWings said:**
> 
I've been thinking about a third mode (... and one to rule them all...) where i use TC0D, TG0D and average, and any of them can drive the fan. This might not eliminate the over shoot, but would certainly give a very safe temperature control.

What do you think?

Good question - sounds like an option that would be safer. 

I haven't compared your Fan control code so I am not sure if its like this or not - however the basic principal sounds good that was put forward by Allan McRae:

> 
To save battery on a laptop, I think that the fan should not come on  when the computer is doing anything less intensive than watching a  movie, so I set that fan to kick in at 65C.  This coincides with what  Mac OSX does.  From OSX, it appears that the fans should hit full speed  at 80C and the speed builds up exponentially to that point.  The formula  I use for changing the fan speed when the temperature is increasing is:
 temp <= 65:
   speed = max(current_speed, 2000)
65 < temp < 80:
   step = (6200 - 2000) / ( (80 - 65) * (80 - 64) / 2 )
   speed = max(current_speed, ceil(2000 + (temp - 65) * (temp - 64) / 2 * step))
temp >= 80:
   speed = 6200
 When the temperature is decreasing, I prefer to keep the fan going  slightly longer to force the temperature down to low levels as quickly  as possible.   I push it back down to 55C using this formula:
 temp >= 80:
   speed = 6200
55 < temp < 80:
   step = (6200 - 2000) / ( (80 - 55) * (80 - 54) / 2 )
   speed = min(current_speed, floor(6200 - (80 - temp) * (81 - temp) / 2 * step)
temp <= 55:
   speed = 2000
Source: [http://allanmcrae.com/2010/05/simple-macbook-pro-fan-daemon/](http://allanmcrae.com/2010/05/simple-macbook-pro-fan-daemon/)

Not sure if this any good either - however it does keep the fan going a tad longer until the machine cooled down a bit more. 

The lower left corner where my palm rests does still feel pretty warm even - even so I think its not different to OS X operation.

Lots of Reviews have pointed out that the MacBooks do get fairly warm.

---

### Post by SwedishWings on 2010-08-27
> **dngfng said:**
> Good question - sounds like an option that would be safer. 

I haven't compared your Fan control code so I am not sure if its like this or not - however the basic principal sounds good that was put forward by Allan McRae:

Source: [http://allanmcrae.com/2010/05/simple-macbook-pro-fan-daemon/](http://allanmcrae.com/2010/05/simple-macbook-pro-fan-daemon/)

Not sure if this any good either - however it does keep the fan going a tad longer until the machine cooled down a bit more.

I checked his code and it is quite different from mine. For one thing, it don't sense the GPU at all. Another difference is that it uses the coretemp module rather than applesmc-dkms (though i think it's needed by coretemp).

I will clean up the code, update the docs, and then do some more work on it. 

> **dngfng said:**
> The lower left corner where my palm rests does still feel pretty warm even - even so I think its not different to OS X operation.

Have you tried to change /etc/macfanctl.conf? If it's too hot, adjust there until you are happy. Please report back the values you find suitable, and i'll try to see how it works on mine.

---

### Post by dngfng on 2010-08-27
Sure will do - could take a while until I have some time to give it a bit of a play.

---

### Post by SwedishWings on 2010-08-28
**EDIT: [Please see this post for new instructions]("http://ubuntuforums.org/showpost.php?p=9793400&postcount=42").**

I released a new version on the PPA, with the following changes:

```
macfanctld (0.2)
  * Fixed bug where only fan 1 got updated.
  * Changed to use sensors TC0P/TG0P instead of TC0D/TC0D that was to noisy.
  * Removed the modes. Now uses TC0P/TG0P and average concurrently.
  * Replaced README with a new man page, macfanctld.1 (enter 'man macfanctld' to read it)

macfanctld (0.1)
  * Updated to GPL 3 in source files.
  * Clean up the code, minor bug fixes.
  * Added code to handle only 1 fan.
  * Removed command line switches -a -d and -s. Moved this settings
    to the config file.
  * Fixed so that HUP signal re-reads config properly.

```
With the above changes, i hope it will work on most MacBooks using applesmc-dkms.

Please test this out and send me feedback.

If you don't want to add my PPA, see the attached deb package, otherwise do this:
```
$ sudo add-apt-repository ppa:mikael-sesamiq/ppa
$ sudo apt-get update
$ sudo apt-get install macfanctld
```
/Mike

---

### Post by dngfng on 2010-08-30
Hi,
haven't installed your update yet - but dropping the kick in tempreture of the Fan to 60 C seemed to smoothen the fan speed transitions better - have to do some long term tests with these settings.

Will have a look at your new code and start testing it later this week.

---

### Post by buntuLo on 2010-08-30
great, so much looking forward to get this installed..
any chance you'll upload a version for Kaarmic (9.10) on your PPA?
also, you may correct the two typos in your previous post: add-apt-get >> apt-get
thanks a lot for your work!

---

### Post by SwedishWings on 2010-08-30
> **buntuLo said:**
> great, so much looking forward to get this installed..
any chance you'll upload a version for Kaarmic (9.10) on your PPA?
also, you may correct the two typos in your previous post: add-apt-get >> apt-get
thanks a lot for your work!

Thanks, corrected the typos above.

There is now a Karmic package on the PPA. I have no Karmic box to test it on, but i guess it'll work just fine. Please let me know if there are any problems.

Cheers,
Mike

---

### Post by buntuLo on 2010-08-30
> **SwedishWings said:**
> There is now a Karmic package on the PPA. I have no Karmic box to test it on, but i guess it'll work just fine. Please let me know if there are any problems.
Mike, thanks again: installed and running on Karmic without any trouble. i'll report back any other issue i may notice using it.
ciao, Lo.

---

### Post by SwedishWings on 2010-08-30
> **dngfng said:**
> Hi,
haven't installed your update yet - but dropping the kick in tempreture of the Fan to 60 C seemed to smoothen the fan speed transitions better - have to do some long term tests with these settings.

Will have a look at your new code and start testing it later this week.

The new code is really much smoother and controls the fan better. The problem of the speed peaks was because the Tx0D/Tx0D sensors were very noisy. I did a dump on all sensors and graphed it, so i know for sure it was that.

Don't bother to trim the old one ;)

Thanks for your input!

---

### Post by dngfng on 2010-08-30
cool - will install the new code via apt-get when i get home. 

Guess I have to perform a make uninstall first since I installed the first version(s) manually.

---

### Post by SwedishWings on 2010-08-30
> **dngfng said:**
> Guess I have to perform a make uninstall first since I installed the first version(s) manually.

Yes, do 'sudo make uninstall' before installing!

Good luck!

---

### Post by SwedishWings on 2010-09-01
**macfanctl has been moved**

macfanctl has been moved to the [mactel PPA]("https://launchpad.net/~mactel-support/+archive/ppa") and has been deleted from my personal PPA.

To make sure you get future updates (if you have installed from my personal PPA), do
```
$ sudo apt-get purge macfanctld
```
Remove ~mikael-sesamiq PPA. (see [https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party%20Software%20Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party%20Software%20Tab))

Assuming that you already have the mactel PPA defined, do

```

$ sudo apt-get update
$ sudo apt-get install macfanctld
```

and you should have a new macfancltd running on your MacBook.

Cheers!

/Mike

---

### Post by linuxopjemac on 2010-09-01
this is so nice! I installed it on my MacBook 2,1 too. See when my fan will kick in....

---

### Post by kosumi68 on 2010-09-03
SwedishWings,

Thank you for you great work with the daemon. Your package solves a long-standing problem for a lot of people. Kudos.

---

### Post by funkwurm on 2010-09-08
I also just wanna express my thanks, specifically to SwedishWings. I'm using your daemon on a MacBookPro1,1 (an oldie indeed) running Lucid and even before the login-screen was there I could hear the fans spin to the 4000 RPM minimum that I'd set it too (I like resting my wrists without burning them).

I read in the man-page that it depends on applesmc-dkms? So I installed that package too in Synaptic, but couldn't you make that a dependency so it's checked automatically when you want to install it?

---

### Post by Engine_number_9 on 2010-09-14
> **funkwurm said:**
> I also just wanna express my thanks, specifically to SwedishWings.

+1.

I'll be installing Ubuntu on a MB 5,1 and I look forward to not having a red hot mac :-)

---

### Post by debb1046 on 2010-09-29
I have a Macbook Pro 3,1 and macfanctl complains about
not being able to read temp1_input. I guess the fan control still works but the log files are cluttered with the corresponding
applesmc: wait status failed: 5 != 0
messages. May be check whether inputs can be read when the daemon starts and not poll the unreadable ones later?

Thanks,
Reiner

---

### Post by SwedishWings on 2010-09-29
> **debb1046 said:**
> I have a Macbook Pro 3,1 and macfanctl complains about
not being able to read temp1_input. I guess the fan control still works but the log files are cluttered with the corresponding
applesmc: wait status failed: 5 != 0
messages. May be check whether inputs can be read when the daemon starts and not poll the unreadable ones later?

Thanks,
Reiner

Is it only "temp1_input" that fails, or do you see other sensors in the log as well? 

The "wait status failed: 5 != 0" has nothing to do with macfanctl, and i can't help with that. I find it annoying too...

Thanks,
Mike

---

### Post by debb1046 on 2010-09-29
I seem to have temp1 to temp13 and they are all readable except for temp1.
The temp1_label says "TALP"
It is definitly trying to read temp1_input which triggers the applesmc error message. When I stop macfanctld the error messages are not appearing. I can also trigger them by just
cat /sys/devices/platform/applesmc.768/temp1_input

---

### Post by SwedishWings on 2010-09-29
> **debb1046 said:**
> I seem to have temp1 to temp13 and they are all readable except for temp1.
The temp1_label says "TALP"
It is definitly trying to read temp1_input which triggers the applesmc error message. When I stop macfanctld the error messages are not appearing. I can also trigger them by just
cat /sys/devices/platform/applesmc.768/temp1_input

Ok, a new problem then. Please edit the config file

```
$ sudo gedit /etc/macfanctl.conf
```

and change 

```
log_level: 0
```
to 
```
log_level: 2
```

Restart the daemon with 

```
$ sudo service macfanctld restart
```

Let it run for 30 min or more and then post (or attach) the contents of /var/log/macfanctl.log.

Thanks,
Mike

---

### Post by debb1046 on 2010-09-30
Thanks. Here's the log.

---

### Post by cath0dez on 2010-10-18
Nevermind.  The more I read about mbp power managment in Linux the more I miss my virtualbox setup.  Back to the drawing board.

---

### Post by aztechclan on 2010-10-25
Hello,
Thanks for building this tool.  However I am still having issues controlling the fan.  It seems that no matter what I tweak in this config file it only pays attention to the Average Temperature.  If I attempt to pin it on the correct sensors it just ignores their input and stays hot.

My current config, just to keep the fan speed up is to bump the average temperature floor/ceiling waaaay down.  Attaching my logs and config.  Any help or suggestions welcome!

---

### Post by Yako no Kai on 2010-10-30
This does not work on an intel mac mini.  The temperature always sticks to the minimum, even when I raise it.

I think the reason why is that it is calculating the temperatures incorrectly.  For example, when unzipping a big file on a test install of maverick, macfanctl.log says ...

Spped: 2000, AVG:28.0
Spped: 2000, AVG:27.8
Spped: 2000, AVG:29.0

Actual CPU temperatures (not caught at the exact same moment, but close enough):
54250, 54000, 56500

As you can see, it looks like the average is about half the actual values.  As if, for example, it is taking the sum of only one of the cpu temps and dividing it by 2.  When I run it in the foreground, it says "Found 2 sensors: TC0D - CPU 0 Die Temp."  That is just one.

Edit: It looks like I assumed that temp 1 and temp 2 were for different cpus.  Apparently one of them is TC0D and the other is TC0P (proximity).  Not sure which is which at the moment, but it means that the division by 2 has nothing to do with the number of cores.  

Edit: Perhaps the bug happens instead because the mac mini uses a nvidia cpu rather than intel. TG0P and TG0T do not exist in the applesmc device, although nvidia-settings is able to read the GPU temp, so it is accessible somehow.  When 2 sensors are detected, macfanctld may be adding them up and dividing them by the default expected number, 4.

It looks like I can get around the problem by setting the values in macfanctl.log with much reduced numbers, but it is tricky to configure when dividing everything in half.

---

### Post by kosumi68 on 2010-10-31
Regarding missing values, I wrote this patch a month ago while reading though the code. It fixes a number of off-by-one errors, maybe it helps.

---

### Post by SwedishWings on 2010-11-01
Hi folks,

Sorry for my absence, been drowning in work the last few weeks.

I have done some work that address the following:

1) Added the patch from kosumi68, that solves the issue that Yako no Kai had above.

2) Added and exclude option to the config file that disables reading of selected sensors (for instance temp1_input). This would solve the flooding of the log file for some users.

The issues with temp1_input eludes me. If anyone knows why certain sensors are not readable, please let me know. I suspect there are bugs in applesmc... kosumi68 - do you have a clue?

I have coded the stuff, but need a little more testing and update the docs before committing to the mactel-support repo. Hopefully done this week.

Again, sorry for being late with this.

/Mike

---

### Post by SwedishWings on 2010-11-01
> **aztechclan said:**
> Hello,
Thanks for building this tool.  However I am still having issues controlling the fan.  It seems that no matter what I tweak in this config file it only pays attention to the Average Temperature.  If I attempt to pin it on the correct sensors it just ignores their input and stays hot.

My current config, just to keep the fan speed up is to bump the average temperature floor/ceiling waaaay down.  Attaching my logs and config.  Any help or suggestions welcome!

I looked in your attached config file, and found several entries that are not supported. Try 
```
$ man macfanctld
```
to find supported options.

I noticed in your log file the the fan runs at max (6200) throughout, and your mac is still quite hot. Have you tried to find ways to get the temp down through other means, like laptop mode etc? Both CPU and GPU runs a lot cooler if you disable desktop effects (System | Preferences | Appearance | Visual Effects -> None).


Regards,
Mike

---

### Post by Nukeador on 2010-11-02
I've a MacBook Pro 6.2 and I had to change the config a bit because fans were too noisy compared with OSX behavior.

With these settings and normal usage I get 2000-2500 rpm
```

fan_min: 2000

temp_avg_floor: 55
temp_avg_ceiling: 65

temp_TC0P_floor: 55
temp_TC0P_ceiling: 65

temp_TG0P_floor: 55
temp_TG0P_ceiling: 65
``` 

I don't know if this change is the best one or if there are other recommended settings for my mbp model.

Regards.

---

### Post by platz on 2010-11-05
I'm not sure the daemon is reading the temperature of my machine correctly. Here's the result of head -n 30 /var/log/macfanctl.log:

```
steve@steve-laptop:~$ head -n 30 /var/log/macfanctl.log 
Using parameters:
    temp_avg_floor: 45
    temp_avg_ceiling: 55
    temp_TC0P_floor: 50
    temp_TC0P_ceiling: 58
    temp_TG0P_floor: 50
    temp_TG0P_ceiling: 58
    fan_min: 2000
    log_level: 2
Found 2 fans.
Found 13 sensors:
    TALP - ?
    TB0T - Battery TS_MAX Temp
    TC0D - CPU 0 Die Temp
    TC0P - CPU 0 Proximity Temp
    TG0H - Left Heat Pipe/Fin Stack Proximity Temp
    TG0P - GPU 0 Proximity Temp
    TG0T - GPU 0 Die - Analog Temp
    TM0P - ?
    TTF0 - ?
    Th0H - ?
    Th1H - ?
    Tm0P - Battery Charger Proximity Temp
Speed: 4200,  AVG: 47.9C, *TC0P: 58.0C,  TG0P: 52.5C, Sensors: TALP:34 TB0T:31 TC0D:76 TC0P:58 TG0H:63 TG0P:52 TG0T:67 TM0P:42 TTF0:65 Th0H:53 Th1H:38 Tm0P:44 
Speed: 4725,  AVG: 47.7C, *TC0P: 59.0C,  TG0P: 53.0C, Sensors: TALP:34 TB0T:31 TC0D:70 TC0P:59 TG0H:63 TG0P:53 TG0T:68 TM0P:42 TTF0:65 Th0H:53 Th1H:38 Tm0P:44 
Speed: 4725,  AVG: 47.5C, *TC0P: 59.0C,  TG0P: 53.2C, Sensors: TALP:34 TB0T:31 TC0D:68 TC0P:59 TG0H:63 TG0P:53 TG0T:67 TM0P:42 TTF0:65 Th0H:53 Th1H:38 Tm0P:44 
Speed: 4725,  AVG: 47.5C, *TC0P: 59.0C,  TG0P: 53.2C, Sensors: TALP:34 TB0T:31 TC0D:67 TC0P:59 TG0H:62 TG0P:53 TG0T:66 TM0P:42 TTF0:65 Th0H:54 Th1H:39 Tm0P:44 
Speed: 4200,  AVG: 47.2C, *TC0P: 58.0C,  TG0P: 53.5C, Sensors: TALP:34 TB0T:31 TC0D:66 TC0P:58 TG0H:62 TG0P:54 TG0T:65 TM0P:42 TTF0:65 Th0H:54 Th1H:39 Tm0P:44 
Speed: 4200,  AVG: 47.2C, *TC0P: 58.0C,  TG0P: 53.8C, Sensors: TALP:34 TB0T:31 TC0D:66 TC0P:58 TG0H:61 TG0P:54 TG0T:65 TM0P:42 TTF0:65 Th0H:54 Th1H:39 Tm0P:44 
Speed: 4200,  AVG: 47.2C, *TC0P: 58.0C,  TG0P: 53.8C, Sensors: TALP:34 TB0T:31 TC0D:66 TC0P:58 TG0H:61 TG0P:54 TG0T:65 TM0P:42 TTF0:65 Th0H:54 Th1H:39 Tm0P:44 

```When is run it with results to stdout, I get the following:

```
steve@steve-laptop:~$ macfanctld -f
Running in foreground, log to stdout.
Using parameters:
    temp_avg_floor: 45
    temp_avg_ceiling: 55
    temp_TC0P_floor: 50
    temp_TC0P_ceiling: 58
    temp_TG0P_floor: 50
    temp_TG0P_ceiling: 58
    fan_min: 2000
    log_level: 2
Found 2 fans.
Found 13 sensors:
    TALP - ?
    TB0T - Battery TS_MAX Temp
    TC0D - CPU 0 Die Temp
    TC0P - CPU 0 Proximity Temp
    TG0H - Left Heat Pipe/Fin Stack Proximity Temp
    TG0P - GPU 0 Proximity Temp
    TG0T - GPU 0 Die - Analog Temp
    TM0P - ?
    TTF0 - ?
    Th0H - ?
    Th1H - ?
    Tm0P - Battery Charger Proximity Temp
Error: Can't open /sys/devices/platform/applesmc.768/fan1_min
Error: Can't open /sys/devices/platform/applesmc.768/fan1_manual
Error: Can't open /sys/devices/platform/applesmc.768/fan2_min
Error: Can't open /sys/devices/platform/applesmc.768/fan2_manual
Speed: 2625,  AVG: 48.4C, *TC0P: 55.0C,  TG0P: 55.0C, Sensors: TALP:43 TB0T:34 TC0D:60 TC0P:55 TG0H:57 TG0P:55 TG0T:60 TM0P:58 TTF0:58 Th0H:55 Th1H:46 Tm0P:49 
Error: Can't open /sys/devices/platform/applesmc.768/fan1_min
Error: Can't open /sys/devices/platform/applesmc.768/fan1_manual
Error: Can't open /sys/devices/platform/applesmc.768/fan2_min
Error: Can't open /sys/devices/platform/applesmc.768/fan2_manual
Speed: 2625,  AVG: 48.4C, *TC0P: 55.0C,  TG0P: 55.0C, Sensors: TALP:43 TB0T:34 TC0D:60 TC0P:55 TG0H:57 TG0P:55 TG0T:60 TM0P:58 TTF0:58 Th0H:55 Th1H:46 Tm0P:49 
Error: Can't open /sys/devices/platform/applesmc.768/fan1_min
Error: Can't open /sys/devices/platform/applesmc.768/fan1_manual
Error: Can't open /sys/devices/platform/applesmc.768/fan2_min
Error: Can't open /sys/devices/platform/applesmc.768/fan2_manual
Speed: 2756,  AVG: 48.4C,  TC0P: 55.0C, *TG0P: 55.2C, Sensors: TALP:43 TB0T:34 TC0D:60 TC0P:55 TG0H:57 TG0P:55 TG0T:60 TM0P:58 TTF0:58 Th0H:55 Th1H:46 Tm0P:49 
Error: Can't open /sys/devices/platform/applesmc.768/fan1_min
Error: Can't open /sys/devices/platform/applesmc.768/fan1_manual
Error: Can't open /sys/devices/platform/applesmc.768/fan2_min
Error: Can't open /sys/devices/platform/applesmc.768/fan2_manual
Speed: 2625,  AVG: 48.4C, *TC0P: 55.0C,  TG0P: 55.0C, Sensors: TALP:43 TB0T:34 TC0D:60 TC0P:55 TG0H:57 TG0P:55 TG0T:60 TM0P:58 TTF0:58 Th0H:55 Th1H:46 Tm0P:49 
^CExiting.

```On and on with the error. Has anyone else seen similar results?

---

### Post by kosumi68 on 2010-11-05
> **platz said:**
> I'm not sure the daemon is reading the temperature of my machine correctly. Here's the result of head -n 30 /var/log/macfanctl.log:
On and on with the error. Has anyone else seen similar results?

Have you tried installing the applesmc in the maverick section of the mactel ppa?

---

### Post by platz on 2010-11-05
> **kosumi68 said:**
> Have you tried installing the applesmc in the maverick section of the mactel ppa?

Yes, I installed it before installing macfanctld.

---

### Post by kosumi68 on 2010-11-05
> **platz said:**
> Yes, I installed it before installing macfanctld.

sudo macfanctld -f ?

Unless that is the problem, I'd really like to see a full scan of your machine, as outlined here: [http://ubuntuforums.org/showthread.php?t=924096](http://ubuntuforums.org/showthread.php?t=924096)

---

### Post by platz on 2010-11-05
> **kosumi68 said:**
> sudo macfanctld -f ?

Unless that is the problem, I'd really like to see a full scan of your machine, as outlined here: [http://ubuntuforums.org/showthread.php?t=924096](http://ubuntuforums.org/showthread.php?t=924096)

Yes, sudoing works to eliminate the errors. I had stopped macfanctld before running the command. After sudo macfanctld -f, there was a short spike in fan speed, now it's leveled-out at 4200, temp avg 50.7. Does that seem normal. Perhaps it is.

---

### Post by SwedishWings on 2010-11-06
> **platz said:**
> Yes, sudoing works to eliminate the errors. I had stopped macfanctld before running the command. After sudo macfanctld -f, there was a short spike in fan speed, now it's leveled-out at 4200, temp avg 50.7. Does that seem normal. Perhaps it is.

That looks normal to me.  The reason macfanctld come to be in the first place was that MacBooks are running very hot without any extra fan control. If you want a lower fan speed, you will get a hotter machine. Do **$ man macfanctld** to see how you can change the parameters if you want to change the defaults.

---

### Post by SwedishWings on 2010-11-06
I have released version 0.4 of macfanctld. It should be available on the mactel-ppa shortly.

**Changes:**
* Patched using Henrik Rydbergs "Off by one" patch.
-- This should solve the problems someone had here with strange average calculations

* Added 'exclude' option to config file. Enables specific sensors to be excluded.
-- This should solve the issues some users have with flooding of the log file for certain unreadable sensors. Note that you must manually add exclusion of sensors in /etc/macfanctl.conf. Se the man page for details.

I heard some rumors that the later problem will be solved in an upcoming version of applesmc-dkms. Looking forward to that!

Cheers,
Mike

---

### Post by platz on 2010-11-06
Thanks for all your work, I just installed the updated version and config file. Everything seems great, at rest temps avg about 53 with fan speed holding between 3600 and 3800. This is a great help. Cheers!

---

### Post by Yako no Kai on 2010-11-07
With kosumi's patch, I can confirm that it seems to be working right with the proper numbers.  Thanks a lot guys.

---

### Post by debb1046 on 2010-11-08
> **SwedishWings said:**
> I have released version 0.4 of macfanctld. It should be available on the mactel-ppa shortly.

* Added 'exclude' option to config file. Enables specific sensors to be excluded.
-- This should solve the issues some users have with flooding of the log file for certain unreadable sensors. Note that you must manually add exclusion of sensors in /etc/macfanctl.conf. Se the man page for details.



Hmm, excluding doesn't do anything here. Daemon still tries to read 
/sys/devices/platform/applesmc.768/temp1_input
no matter what number I put in the exclude:

---

### Post by SwedishWings on 2010-11-08
> **debb1046 said:**
> Hmm, excluding doesn't do anything here. Daemon still tries to read 
/sys/devices/platform/applesmc.768/temp1_input
no matter what number I put in the exclude:

Did you update?

---

### Post by debb1046 on 2010-11-09
I believe so, otherwise I wouldn't have seen the exclude line in the config file. The version is 0.4~mactel1~lucid

---

### Post by SwedishWings on 2010-11-09
> **debb1046 said:**
> I believe so, otherwise I wouldn't have seen the exclude line in the config file. The version is 0.4~mactel1~lucid

How do you know that it's reading temp1_input? Please give some more details.

Thanks,
Mike

---

### Post by debb1046 on 2010-11-11
I hope I'm not doing this wrong. I put in /etc/macfanctl.conf:
```
excluded: 1
```I get the following lines in macfanctl.log:

Using parameters:
        temp_avg_floor: 35
        temp_avg_ceiling: 45
        temp_TC0P_floor: 50
        temp_TC0P_ceiling: 58
        temp_TG0P_floor: 50
        temp_TG0P_ceiling: 58
        fan_min: 2000
        log_level: 2
Found 2 fans.
Found 13 sensors:
         1: TALP - ?
         2: TB0T - Battery TS_MAX Temp
         3: TC0D - CPU 0 Die Temp
         4: TC0P - CPU 0 Proximity Temp
         5: TG0D - GPU Die - Digital
         6: TG0H - Left Heat Pipe/Fin Stack Proximity Temp
         7: TTF0 - ?
         8: TW0P - ?
         9: Th0H - ?
        10: Th1H - ?
        11: Th2H - Right Fin Stack Proximity Temp
        12: Tm0P - Battery Charger Proximity Temp
        13: Ts0P - Palm Rest Temp
Error: Can't read  /sys/devices/platform/applesmc.768/temp1_input
Speed: 2956, *AVG: 42.0C,  TC0P: 44.0C, Sensors: TALP:0 TB0T:32 TC0D:46 TC0P:44 TG0D:56 TG0H:47 TTF0:70 TW0P:47 Th0H:48 Th1H:39 Th2H:40 Tm0P:46 Ts0P:33
Error: Can't read  /sys/devices/platform/applesmc.768/temp1_input
Speed: 2948, *AVG: 42.0C,  TC0P: 44.0C, Sensors: TALP:0 TB0T:32 TC0D:46 TC0P:44 TG0D:56 TG0H:47 TTF0:70 TW0P:47 Th0H:48 Th1H:39 Th2H:40 Tm0P:46 Ts0P:33

---

### Post by SwedishWings on 2010-11-15
> **debb1046 said:**
> I hope I'm not doing this wrong. I put in /etc/macfanctl.conf:
```
excluded: 1
```...

The configuration file is wrong. Please replace
```
excluded: 1
```
with 
```
exclude: 1
```
My mistake, will update the ppa later on. Meanwhile, just edit /etc/macfanctl.conf manually.

---

### Post by debb1046 on 2010-11-17
Works now. Thanks!

---

### Post by tp21 on 2010-11-20
hi,
i have macbook pro 4.1 running ubuntu 10.10, i just tried macfanctld and i have the following errors:
hm@orbit:~$ head -n 30 /var/log/macfanctl.log 
Using parameters:
	temp_avg_floor: 45
	temp_avg_ceiling: 55
	temp_TC0P_floor: 50
	temp_TC0P_ceiling: 58
	temp_TG0P_floor: 50
	temp_TG0P_ceiling: 58
	fan_min: 2000
	log_level: 0
Found 2 fans.
Found 14 sensors:
	 1: TB0T - Battery TS_MAX Temp 
	 2: TC0D - CPU 0 Die Temp 
	 3: TC0P - CPU 0 Proximity Temp 
	 4: TG0D - GPU Die - Digital 
	 5: TG0H - Left Heat Pipe/Fin Stack Proximity Temp 
	 6: TG0V - ? 
	 7: TGTV - ? 
	 8: TTF0 - ? 
	 9: TW0P - ? 
	10: Th0H - ? 
	11: Th1H - ? 
	12: Th2H - Right Fin Stack Proximity Temp 
	13: Tm0P - Battery Charger Proximity Temp 
	14: Ts0P - Palm Rest Temp 
Error: Can't read  /sys/devices/platform/applesmc.768/temp2_input
Error: Can't read  /sys/devices/platform/applesmc.768/temp5_input
Error: Can't read  /sys/devices/platform/applesmc.768/temp12_input
Error: Can't read  /sys/devices/platform/applesmc.768/temp12_input
Error: Can't read  /sys/devices/platform/applesmc.768/temp9_input

i am not sure that my fan works at all, how can i check this?
thanks

---

### Post by SwedishWings on 2010-11-20
> **tp21 said:**
> Error: Can't read  /sys/devices/platform/applesmc.768/temp2_input
Error: Can't read  /sys/devices/platform/applesmc.768/temp5_input
Error: Can't read  /sys/devices/platform/applesmc.768/temp12_input
Error: Can't read  /sys/devices/platform/applesmc.768/temp12_input
Error: Can't read  /sys/devices/platform/applesmc.768/temp9_input

i am not sure that my fan works at all, how can i check this?
thanks

The errors are normal. You get them because applesmc-dkms blocks reading while reading the sensors.

If you want to see more on what is going, edit /etc/macfanctl.conf and change "log_level" to 1 or 2. 

Also, see the man page for macfanctld for more info.

---

### Post by tp21 on 2010-11-20
thanks.
after changing log-level to 2, i receive this:
Using parameters:
	temp_avg_floor: 45
	temp_avg_ceiling: 55
	temp_TC0P_floor: 50
	temp_TC0P_ceiling: 58
	temp_TG0P_floor: 50
	temp_TG0P_ceiling: 58
	fan_min: 2000
	log_level: 2
Found 2 fans.
Found 14 sensors:
	 1: TB0T - Battery TS_MAX Temp 
	 2: TC0D - CPU 0 Die Temp 
	 3: TC0P - CPU 0 Proximity Temp 
	 4: TG0D - GPU Die - Digital 
	 5: TG0H - Left Heat Pipe/Fin Stack Proximity Temp 
	 6: TG0V - ? 
	 7: TGTV - ? 
	 8: TTF0 - ? 
	 9: TW0P - ? 
	10: Th0H - ? 
	11: Th1H - ? 
	12: Th2H - Right Fin Stack Proximity Temp 
	13: Tm0P - Battery Charger Proximity Temp 
	14: Ts0P - Palm Rest Temp 
Speed: 2000,  AVG: 45.8C,  TC0P: 46.2C, Sensors: TB0T:23 TC0D:58 TC0P:46 TG0D:62 TG0H:51 TG0V:50 TGTV:65 TTF0:70 TW0P:37 Th0H:47 Th1H:34 Th2H:36 Tm0P:38 Ts0P:26 
Speed: 2000,  AVG: 45.5C,  TC0P: 46.5C, Sensors: TB0T:23 TC0D:54 TC0P:46 TG0D:59 TG0H:51 TG0V:50 TGTV:65 TTF0:70 TW0P:38 Th0H:48 Th1H:34 Th2H:36 Tm0P:38 Ts0P:26 
Speed: 2000,  AVG: 45.4C,  TC0P: 46.5C, Sensors: TB0T:23 TC0D:51 TC0P:46 TG0D:59 TG0H:51 TG0V:50 TGTV:65 TTF0:70 TW0P:38 Th0H:48 Th1H:34 Th2H:36 Tm0P:38 Ts0P:26 
Speed: 2000,  AVG: 45.6C,  TC0P: 46.5C, Sensors: TB0T:23 TC0D:50 TC0P:46 TG0D:60 TG0H:51 TG0V:50 TGTV:66 TTF0:70 TW0P:40 Th0H:48 Th1H:34 Th2H:36 Tm0P:38 Ts0P:26 
Speed: 2000,  AVG: 45.5C,  TC0P: 46.5C, Sensors: TB0T:23 TC0D:50 TC0P:46 TG0D:59 TG0H:50 TG0V:50 TGTV:66 TTF0:70 TW0P:40 Th0H:48 Th1H:34 Th2H:36 Tm0P:38 Ts0P:26 

does this mean that the fan is currently spinning with speed 2000? i am wondring because i can hardly hear it.

---

### Post by SwedishWings on 2010-11-20
> **tp21 said:**
> does this mean that the fan is currently spinning with speed 2000? i am wondring because i can hardly hear it.

Yes, all seem fine, the fans are very quiet. 

If your MacBook feels hot, you can always tweak the config file.

---

### Post by ilazria on 2010-12-08
Thank you so much for this! I just installed this on my first gen Mac Pro (not MacBook) I had all but given up on using Ubuntu on my Mac Pro. Now I don't have to worry about burning out my video card.

---

### Post by SwedishWings on 2010-12-09
Happy to help \\:D/

---

### Post by oneleaftea on 2011-03-26
Thanks for this! I just installed applesmc.dkms and macfanctld. I ran it with -f and all seems normal. It feel like it is not as hot as it was before on this Macbook 4.1.

What is the proper way to use macfanctld? Does it need to be run everytime I startup? Sorry for being such a newbie, but what is the best way to do that? Thanks!

---

### Post by SwedishWings on 2011-03-27
> **oneleaftea said:**
> What is the proper way to use macfanctld? Does it need to be run everytime I startup? Sorry for being such a newbie, but what is the best way to do that? Thanks!

If you are using the [mactel PPA]("https://launchpad.net/~mactel-support/+archive/ppa"), just install it from there. It will automatically start up on boot:

```
$ sudo apt-get install macfanctld
```

---

### Post by oneleaftea on 2011-03-27
cool thanks!

So from reading about macfanctld, I tried monitoring the temps and got this:

```
$ tail -F /var/log/macfanctl.log
	 2: TC0D - CPU 0 Die Temp 
	 3: TC0P - CPU 0 Proximity Temp 
	 4: TM0P - ? 
	 5: TN0P - MCP Proximity 
	 6: TTF0 - ? 
	 7: TW0P - ? 
	 8: Th0H - ? 
	 9: Th0S - ? 
	10: Th1H - ? 
Error: Can't read  /sys/devices/platform/applesmc.768/temp4_input
Error: Can't read  /sys/devices/platform/applesmc.768/temp3_input
Error: Can't read  /sys/devices/platform/applesmc.768/temp3_input
Error: Can't read  /sys/devices/platform/applesmc.768/temp3_input
Error: Can't read  /sys/devices/platform/applesmc.768/temp4_input
Error: Can't read  /sys/devices/platform/applesmc.768/temp3_input

```

I guess these errors are normal according to this thread. Does anything look out of the ordinary?

Put in log level 1 and now read these:

Speed: 2000,  AVG: 47.4C,  TC0P: 47.2C
Speed: 2000,  AVG: 47.3C,  TC0P: 47.0C
Speed: 2000,  AVG: 47.3C,  TC0P: 46.8C
Speed: 2000,  AVG: 47.4C,  TC0P: 46.8C
Speed: 2000,  AVG: 47.2C,  TC0P: 46.5C
Speed: 2000,  AVG: 47.0C,  TC0P: 46.5C
Speed: 2000,  AVG: 46.9C,  TC0P: 46.2C
Speed: 2000,  AVG: 46.8C,  TC0P: 46.0C
Speed: 2000,  AVG: 46.7C,  TC0P: 46.0C
Speed: 2000,  AVG: 46.9C,  TC0P: 45.8C
Speed: 2000,  AVG: 47.1C,  TC0P: 46.2C
Speed: 2000,  AVG: 47.1C,  TC0P: 46.0C
Speed: 2000,  AVG: 47.1C,  TC0P: 46.2C
Speed: 2000,  AVG: 47.8C,  TC0P: 46.2C
Speed: 2000,  AVG: 47.9C,  TC0P: 46.5C
Speed: 2000,  AVG: 47.8C,  TC0P: 46.8C
Speed: 2000,  AVG: 47.7C,  TC0P: 47.0C
Speed: 2000,  AVG: 47.5C,  TC0P: 47.0C
Speed: 2000,  AVG: 47.5C,  TC0P: 47.0C


Seems to be working. :)

---

### Post by smithjc1 on 2011-04-25
Just a quick question for SwedishWings,

After installing 10.10 and using it for a while I went ahead and downloaded the daemon you wrote for my iMac, 24" aluminum model. It seems to be working fine and is doing a decent job at keeping the temperature down. However when the temp does get a little bit higher and the fans rev up I can feel the back of the computer and the right fan on the top is going full speed while the left fan doesn't seem to be doing anything. Is there a way for me to get this to be controlled by the daemon as well?

Thanks!

---

### Post by SwedishWings on 2011-05-02
> **smithjc1 said:**
> Just a quick question for SwedishWings,

After installing 10.10 and using it for a while I went ahead and downloaded the daemon you wrote for my iMac, 24" aluminum model. It seems to be working fine and is doing a decent job at keeping the temperature down. However when the temp does get a little bit higher and the fans rev up I can feel the back of the computer and the right fan on the top is going full speed while the left fan doesn't seem to be doing anything. Is there a way for me to get this to be controlled by the daemon as well?

Thanks!

Can you post the macfanctld log please? 

Regards,
Mike

---

### Post by jerrycal on 2011-05-07
Hi, I had macfanctld running on Lucid and Maverick but now after upgrading to Natty apple-smc and macfanctld are nowhere to be found... I added ppa:mactel-support and even ppa:mactel-support/ppa and no luck...
Any ideas?
Thank you

---

### Post by SwedishWings on 2011-05-07
> **jerrycal said:**
> Hi, I had macfanctld running on Lucid and Maverick but now after upgrading to Natty apple-smc and macfanctld are nowhere to be found... I added ppa:mactel-support and even ppa:mactel-support/ppa and no luck...
Any ideas?
Thank you

I have not had time to fix this, will try to find time tomorrow.

Regards,
Mike

---

### Post by jerrycal on 2011-05-07
> **SwedishWings said:**
> I have not had time to fix this, will try to find time tomorrow.

Regards,
Mike

No problem. I was just wondering if it was still needed on Natty, because during upgrade it said removing no longer needed packages, and among them was "apple-smc". But then on Ubuntu documentation page it did say that Temperature sensors needed some extra add on. So far it runs really smooth and no extra heat...
Anyway, no rush and thanks for the great product.

---

### Post by Macareno on 2011-05-07
I installed manually:
  macfanctld_0.5~mactel1~maverick_amd64.deb
.. in my macbook pro 7.1 with ubuntu Natty and it works well.

In the description from macfanctld shows:
"Important: macfanctld depends on applesmc-dkms." .. but I didn't install it and works well.

Thanks.

---

### Post by jerrycal on 2011-05-07
> **Macareno said:**
> I installed manually:
  macfanctld_0.5~mactel1~maverick_amd64.deb
.. in my macbook pro 7.1 with ubuntu Natty and it works well.

In the description from macfanctld shows:
"Important: macfanctld depends on applesmc-dkms." .. but I didn't install it and works well.

Thanks.

Cool...I added Maverick repo and was able to get the applesmc-dkms and then macfanctld, then changed the min speed to 3000 and seems like its working:

sudo macfanctld -f returns:

Running in foreground, log to stdout.
Using parameters:
    temp_avg_floor: 45
    temp_avg_ceiling: 55
    temp_TC0P_floor: 50
    temp_TC0P_ceiling: 58
    temp_TG0P_floor: 50
    temp_TG0P_ceiling: 58
    fan_min: 3000
    log_level: 0
Found 1 fan.
Found 14 sensors:
     1: TB0T - Battery TS_MAX Temp 
     2: TB1T - Battery TS1 Temp 
     3: TB2T - Battery TS2 Temp 
     4: TB3T - Battery Temp 
     5: TC0D - CPU 0 Die Temp 
     6: TC0P - CPU 0 Proximity Temp 
     7: TN0D - MCP Die 
     8: TN0P - MCP Proximity 
     9: TTF0 - ? 
    10: Th0H - ? 
    11: Th1H - ? 
    12: ThFH - ? 
    13: Ts0P - Palm Rest Temp 
    14: Ts0S - ?

---

### Post by samuaz on 2011-05-09
I have problems on a macbook 4.1 with ubuntu natty 11.04
1. First install lm-sensors and add the CoreTemp to the module /etc/module
2. Next install the (applesmc-dkms) manually
3. then install the macfanctl manually, as indicated by the Ubuntu help guide for my macbook
4. change options to the macfanctl.conf, for the sensors using my macbook, which are the two processor, my gpu is integrated and sensor do not show me to her (gma x3100).

Found 10 sensors:
1: TB0T - Battery Temp TS_MAX *** *** EXCLUDED
2: TC0D - Die Temp CPU 0 ---> CPU on my MacBook
3: TC0P - Proximity Temp CPU 0 ---> CPU on my MacBook
4: TM0P -? EXCLUDED *** ***
5: TN0P - MCP Proximity *** *** EXCLUDED
6: TTF0 -? EXCLUDED *** ***
7: TW0P -? EXCLUDED *** ***
8: Th0H -? EXCLUDED *** ***
9: Th0S -? EXCLUDED *** ***
10: Th1H -? EXCLUDED *** ***

the others the excluded: 1 4 5 6 7 8 9 10

then increase slightly to values &#8203;&#8203;that were more like osx, osx keeps the fans to 1800 rpm idle speed when they are between 40-60 degrees Celsius then progressively increasing and if they reach 70 the fan increases to full speed 6200 rpm in osx is really smooth the fans do not listen unless it is firing at full speed

temp_avg_floor: 50 # 45
temp_avg_ceiling: 70 # 55

temp_TC0P_floor: 65 # 50
temp_TC0P_ceiling: 70 # 58

temp_TG0D_floor: 65 # 50 ---------> My gpu is integrated x3100 do not have this sensor
temp_TG0D_ceiling: 70 # 58

at first I worked all right, but in a couple of restarts stopped working and the fans are always 6200 rpm but mi macbook its at 50 degrees Celsius, which happened? some solution someone help me please!

other important question the CoreTemp show a lower temperature than the TCOD And TCOP, and I have a sensor to 71.5 degrees, do not know where is!

samuel @ samuel-MacBook: ~ $ sensors
CoreTemp-isa-0000
Adapter: ISA adapter
Core 0: +48.0 &#1058;&#1040;C (high = +105.0 &#1058;&#1040;C, crit = +105.0 &#1058;&#1040;C)

CoreTemp-isa-0001
Adapter: ISA adapter
Core 1: +48.0 &#1058;&#1040;C (high = +105.0 &#1058;&#1040;C, crit = +105.0 &#1058;&#1040;C)

applesmc-isa-0300
Adapter: ISA adapter
Exhaust: 6216 RPM (min = 2000 RPM)
TB0T: +34.5 &#1058;&#1040;C
TC0D: +56.8 &#1058;&#1040;C
TC0P: +54.2 &#1058;&#1040;C
TM0P: +58.8 &#1058;&#1040;C
TN0P: +54.2 &#1058;&#1040;C
TTF0: +50.0 &#1058;&#1040;C
TW0P: +71.5 &#1058;&#1040;C ------------------> SENSOR THAT I HAVE NO IDEA IS THIS, BUT THIS WORRIES ME TO 71.5 DEGREES anyone knows anything about it?
Th0H: +54.8 &#1058;&#1040;C
Th0S: +54.8 &#1058;&#1040;C
Th1H: +54.8 &#1058;&#1040;C

which is the correct temperature and TCOP TCOD or CoreTemp?, some way to make use of CoreTemp, if these are the right ones?

I attach the log:
samuel @ samuel-MacBook: ~ $ cat / var / log / macfanctl.log
Using parameters:
temp_avg_floor: 50
temp_avg_ceiling: 70
temp_TC0P_floor: 65
temp_TC0P_ceiling: 70
temp_TG0P_floor: 65
temp_TG0P_ceiling: 80
fan_min: 2000
exclude: temp1_input temp4_input temp5_input temp6_input temp7_input temp8_input temp9_input temp10_input
log_level: 2
Found 1 fan.
Found 10 sensors:
1: TB0T - Battery Temp TS_MAX *** *** EXCLUDED
2: TC0D - CPU 0 Die Temp
3: TC0P - CPU 0 Temp Proximity
4: TM0P -? EXCLUDED *** ***
5: TN0P - MCP Proximity *** *** EXCLUDED
6: TTF0 -? EXCLUDED *** ***
7: TW0P -? EXCLUDED *** ***
8: Th0H -? EXCLUDED *** ***
9: Th0S -? EXCLUDED *** ***
10: Th1H -? EXCLUDED *** ***
Speed: 2000 AVG: 55.0C, TC0P: 53.5C, Sensors: TC0D: 56 TC0P: 54
Speed: 2000 AVG: 54.1C, TC0P: 53.5C, Sensors: TC0D: 55 TC0P: 54
Speed: 2000 AVG: 54.5C, TC0P: 53.5C, Sensors: TC0D: 56 TC0P: 54
Speed: 2000 AVG: 54.5C, TC0P: 53.5C, Sensors: TC0D: 56 TC0P: 54
Speed: 2000 AVG: 54.8C, TC0P: 53.2C, Sensors: TC0D: 56 TC0P: 53

shows a speed of 2000 but my fan is at 6200 rpm a temperature that is All in apparently normal for my Mac, CoreTemp sensors show a temperature of 49 degrees while TCOD/0P show 53 to 54 degrees Celsius, and even so at 6200 rpm while the temperature does not drop to that, restarting in OSX I put the fan at 6200 rpm and shows a temperature of 49-50 degrees similar to that of CoreTemp, CoreTemp Apparently is the sensor used to move the fans in osx in my macbook 4.1 ...

my fan is always at 6200 rpm and my battery cry from it, someone please help me, its my first ubuntu installation!

do not know if the problem is this sensor TW0P: &#1058;&#1040;C + 70.0, 70 degrees!
What sensor is it?

Greetings and thanks in advance

*** EDIT: TW0P ITS A WIRELESS MODULE, AIRPORT CARD AND 70º ITS NORMAL TEMPERATURE IN MACS YEA!! LOL BUTS ITS NORMAL AIRPORT ON TEMPERATURE FUCKYOUUUUU APPLE!!!

---

### Post by samuaz on 2011-05-10
I've solved! [http://ubuntuforums.org/showthread.php?p=10795052#post10795052](http://ubuntuforums.org/showthread.php?p=10795052#post10795052)

---

### Post by pratik.ac on 2011-07-04
Help!!

I installed macfanctld v0.2 first. It seems that it takes control of the fan management and when I remove it (because I felt that a threshold of 60 deg is too less for the 2011 Macbook Pro), it leaves the fans uncontrolled at the current speed. In my case, the fans are still running at 4K rpm. Can you please tell me how to let ubuntu handle the fan control like default? I feel that was much better.

---

### Post by SwedishWings on 2011-08-18
Sorry for the delay. macfanctld is now available for Natty from mactel PPA.

/Mike

---

### Post by joskapista on 2011-08-19
Thanks!

---

### Post by ghl on 2011-09-10
Hi, bit of a newbie and got this sort of working but a couple of questions...
using the ppa of mactel-support on my Ubuntu 10.04 LTS, added to the sources using;
deb [http://ppa.launchpad.net/mactel-support/ppa/ubuntu](http://ppa.launchpad.net/mactel-support/ppa/ubuntu) lucid main

If I set the min fan speed to say 6200 when I reboot, the new fan speed is used so it
runs up fine and allows me to change the min rpm in /etc/macfanctl.conf to 3000, see below;
[I]mob@mob-mac:/etc$ cat macfanctl.conf 
# Config file for macfanctl daemon
#
# Note: 0 < temp_X_floor < temp_X_ceiling
#       0 < fan_min < 6200       
fan_min: 3000
temp_avg_floor: 40
temp_avg_ceiling: 50
temp_TC0D_floor: 30
temp_TC0D_ceiling: 55
temp_TG0T_floor: 30
temp_TG0T_ceiling: 55
# Add sensors to be excluded here, separated by space, i.e.
# exclude: 1 7
# will disable reading of sensors temp1_input and temp7_input.
exclude:
# log_level values:
#   0: Startup / Exit logging only
#   1: Basic temp / fan logging
#   2: Log all sensors  
log_level: 0
mob@mob-mac:/etc$ [/I]

The problem is that I changed the sensor to use and also the floor and ceiling values to keep it running as cool as possible, but looking at the log file (/var/log/macfanctl.log), I get;[I]
mob@mob-mac:/etc$ head -n 30 /var/log/macfanctl.log 
Using parameters:
    temp_avg_floor: 40
    temp_avg_ceiling: 50
    temp_TC0P_floor: 50
    temp_TC0P_ceiling: 65
    temp_TG0P_floor: 65
    temp_TG0P_ceiling: 80
    fan_min: 3000
    log_level: 0
Found 2 fans.
Found 12 sensors:
     1: TB0T - Battery TS_MAX Temp 
     2: TC0D - CPU 0 Die Temp 
     3: TC0P - CPU 0 Proximity Temp 
     4: TG0H - Left Heat Pipe/Fin Stack Proximity Temp 
     5: TG0P - GPU 0 Proximity Temp 
     6: TG0T - GPU 0 Die - Analog Temp 
     7: TM0P - ? 
     8: TTF0 - ? 
     9: Th0H - ? 
    10: Th1H - ? 
    11: Tm0P - Battery Charger Proximity Temp 
    12: Ts0P - Palm Rest Temp 
Exiting.[/I]

As you can see the [I]
temp_TC0D_floor: 30
temp_TC0D_ceiling: 55
  temp_TG0T_floor: 30
temp_TG0T_ceiling: 55[/I]

have been ignored (but the fan_min value hasn't), as it's still using;

[I] temp_TC0P_floor: 50
temp_TC0P_ceiling: 65
temp_TG0P_floor: 65
temp_TG0P_ceiling: 80
[/I]
Any ideas how I can change these values please anyone??

currently changing by opening a terminal and doing sudo gedit /etc/macfanctl.conf
making the changes and saving as it looks by the fact that I can cat the file that it's using at least the min fan from this file but not the TC0D or TG0T fields or values.

---

### Post by SwedishWings on 2011-09-15
> **ghl said:**
>     
fan_min: 3000
temp_avg_floor: 40
temp_avg_ceiling: 50
temp_TC0D_floor: 30
temp_TC0D_ceiling: 55
temp_TG0T_floor: 30
temp_TG0T_ceiling: 55


You are trying to add parameters that are not used in macfanctld. Read the man page:
```
$ man macfanctld
```

There you can see what parameters you can change and what they do.

Is your machine getting too hot? For what reason are you trying to change the default?


Regards,
Mike

---

### Post by ghl on 2011-09-16
Hi, thanks for the reply. I was changing sensors as they were the one's that seemed to be the hottest and my mac was occasionally crashing. But... I think I've found the source of the crashing now and fixed (separate software problem) and although I've set the limits very tight, the fans are running at about 2500-4500 rpm, averaging at about 3300 rpm and keeping CPU0 and CPU1 at around 50 Deg.C as reported by the GKrellM gui.

Generally, this is working a treat and now got isight working (albeit not in Skype yet - just black screen). Would be lovely to get the lit keyboard working but that's may be pushing it a bit far! (Macbook Pro)

So it gives me a very solid laptop, running cool and possible to put on my lap without having to worry about blocking air ducts in the base. I have Ubuntu 10.04 LTS on it with WinXP in VirtualBox, Mac OS and possibilities of Parallels on a dual boot - all bases covered.
Just need to get used to trying to find the 'missing' keys on the keyboard such as 'Hash' - can't type it as I can't find it :)

Current settings are;
fan_min: 2000
temp_avg_floor: 30
temp_avg_ceiling: 50
temp_TC0P_floor: 30
temp_TC0P_ceiling: 50
temp_TG0P_floor: 30
temp_TG0P_ceiling: 50

---

### Post by ulicigabriel on 2011-10-27
when i run this command macfanctld -f
 i receive this
[PHP]Running in foreground, log to stdout.
Using parameters:
	temp_avg_floor: 45
	temp_avg_ceiling: 55
	temp_TC0P_floor: 50
	temp_TC0P_ceiling: 58
	temp_TG0P_floor: 50
	temp_TG0P_ceiling: 58
	fan_min: 2000
	log_level: 0
Found applesmc at /sys/devices/platform/applesmc.768
Found 1 fan.
Found 10 sensors:
	 1: TB0T - Battery TS_MAX Temp 
	 2: TC0D - CPU 0 Die Temp 
	 3: TC0P - CPU 0 Proximity Temp 
	 4: TM0P - ? 
	 5: TN0P - MCP Proximity 
	 6: TTF0 - ? 
	 7: TW0P - ? 
	 8: Th0H - ? 
	 9: Th0S - ? 
	10: Th1H - ? 
Error: Can't open /sys/devices/platform/applesmc.768/fan1_min
Error: Can't open /sys/devices/platform/applesmc.768/fan1_manual
Error: Can't open /sys/devices/platform/applesmc.768/fan1_min
Error: Can't open /sys/devices/platform/applesmc.768/fan1_manual
Error: Can't open /sys/devices/platform/applesmc.768/fan1_min
Error: Can't open /sys/devices/platform/applesmc.768/fan1_manual
Error: Can't open /sys/devices/platform/applesmc.768/fan1_min
Error: Can't open /sys/devices/platform/applesmc.768/fan1_manual
Error: Can't open /sys/devices/platform/applesmc.768/fan1_min
Error: Can't open /sys/devices/platform/applesmc.768/fan1_manual
[/PHP]
and still going


then when i i do the same command with "sudo" it is working but after sometime i receive this 
[PHP]Error: Can't read  /sys/devices/platform/applesmc.768/temp8_input
Error: Can't read  /sys/devices/platform/applesmc.768/temp3_input
Error: Can't read  /sys/devices/platform/applesmc.768/temp5_input[/PHP]


and my fans are running all the time between 3000 and 4000 when the cpu temp is between 50-53

---

### Post by Finchj on 2012-12-30
Hate to dig up an old thread, but I've been a bit worried about one of the sensor readings on my Macbook Pro 7.1 running Ubuntu 12.04. I'm very new to Linux and I've tried searching quite a bit for an answer to this, but... haven't seemed to find anything.

I've installed macfanctl and for the most part, everything seems to be under control- except one sensor.

Here is a readout from terminal when I type in sensors:

> finchj@JoshuaFinchmacbookpro:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +43.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +44.0°C  (high = +105.0°C, crit = +105.0°C)

applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :   2004 RPM  (min = 2000 RPM)
TB0T:         +29.0°C  
TB1T:         +29.0°C  
TB2T:         +28.8°C  
TC0D:         +45.8°C  
TC0P:         +41.5°C  
TN0D:         +43.0°C  
TN0P:         +35.2°C  
TN0S:         +51.2°C  
TN1D:         +50.0°C  
TN1F:         +51.2°C  
**TN1G:         +90.0°C  **
TN1S:         +51.2°C  
Th1H:         +39.8°C  
Ts0P:         +27.2°C  
Ts0S:         +34.8°C  


TN1G always seems to be at +90 C. Is this cause for concern?

Here is my log from macfanctl:

> Using parameters:
	temp_avg_floor: 45
	temp_avg_ceiling: 55
	temp_TC0P_floor: 50
	temp_TC0P_ceiling: 58
	temp_TG0P_floor: 50
	temp_TG0P_ceiling: 58
	fan_min: 2000
	log_level: 0
Found applesmc at /sys/devices/platform/applesmc.768
Found 1 fan.
Found 15 sensors:
	 1: TB0T - Battery TS_MAX Temp 
	 2: TB1T - Battery TS1 Temp 
	 3: TB2T - Battery TS2 Temp 
	 4: TC0D - CPU 0 Die Temp 
	 5: TC0P - CPU 0 Proximity Temp 
	 6: TN0D - MCP Die 
	 7: TN0P - MCP Proximity 
	 8: TN0S - ? 
	 9: TN1D - ? 
	10: TN1F - ? 
	11: TN1G - ? 
	12: TN1S - ? 
	13: Th1H - ? 
	14: Ts0P - Palm Rest Temp 
	15: Ts0S - ? 

I know you all are always bombarded with questions, but I thought I'd ask before anything goes wrong with this computer!

---

### Post by cj123 on 2013-01-02
Is it odd that this sensor could be so hot without heating the sensors around it? People have suggested in other forums that strange readings might be malfunctions--though I can't vouch for this view (only responding because no one else is.) Is your computer hot to the touch? It would be good to know what TN1G is. Anyone have a list that includes it. Someone linked to a document with a list in an earlier forum but the link is dead. I imagine it wouldn't be up-to-date anyway.

---

