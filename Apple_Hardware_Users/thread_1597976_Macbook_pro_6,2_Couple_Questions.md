---
title: "Macbook pro 6,2 Couple Questions"
date: 2010-10-15
forum: Apple Hardware Users
---

### Post by Rodimus Prime on 2010-10-15
So I finally installed Ubuntu on my macbook pro.

I had a few questions about senors applet.

I added coretemp the modules and sensors applet only shows me two core's temp? Where are the other two?

Here is the sensors output : 

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +47.0°C  (high = +95.0°C, crit = +105.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +48.0°C  (high = +95.0°C, crit = +105.0°C)  

applesmc-isa-0300
Adapter: ISA adapter
Left side  :1981 RPM  (min = 2000 RPM)
Right side :2009 RPM  (min = 2000 RPM)
TB0T:        +34.0°C                                    
TB1T:        +34.0°C                                    
TB2T:        +31.5°C                                    
TC0C:        +48.5°C                                    
TC0D:        +51.8°C                                    
TC0P:        +51.0°C                                    
TC1C:        +53.0°C                                    
TG0D:        +49.5°C                                    
TG0P:        +49.2°C                                    
TG0T:        +51.8°C                                    
TMCD:        +53.0°C                                    
TP0P:        +57.8°C                                    
TPCD:        +66.0°C                                    
Th1H:        +46.5°C                                    
Th2H:        +45.8°C                                    
Tm0P:        +49.5°C                                    
Ts0P:        +30.0°C                                    
Ts0S:        +40.0°C  


Also sometimes the sensors applet gives me a error saying 'An error occurred while trying to update the value of the sensor Right side  located at sensor://applesmc-isa-0300/2.' but it doesn't show up again - I am assuming its referring to the right fan. Is there something wrong with my right fan sensor? It seems to work fine before and after the error. I don't know why it shows up.


Also I installed gnome-alsamixer. For some reason my headphone jacks red light stays on. It only goes off when I turn off IEC958. But it doesn't remmeber setting after a reboot. Any solutions?

---

### Post by Rodimus Prime on 2010-10-16
Update : so I removed sensors-applet and then reinstalled it. It then gave me an error for the left fan!

---

### Post by pantropik on 2010-10-16
I'm not sure what you're asking. Why would it show more than two cores on a dual core machine? There are no quad core Macbook Pros, only dual core with hyperthreading, meaning you have two physical cores, each of which can "split in half" to work on two threads for a total of four *logical* cores.

EDITED to add:

As for the red light, I found it would come on at random times even after being turned off so I just wrote a script to turn it off and then set up a CTRL-ALT-O hotkey in GNOME keyboard preferences that linked to that script. So any time I noticed the glowy red eye I could just hit that combo and kill it. 

Make a file with the following contents (I make ~/.bin/ directory for my scripts):

amixer set IEC958 off 

Then make the file executable:

chmod +x /path/to/script/script

Then assign a key combo in keyboard shortcuts to run that script. Keep in mind that the IEC958 is case sensitive.

---

### Post by Rodimus Prime on 2010-10-16
> **pantropik said:**
> I'm not sure what you're asking. Why would it show more than two cores on a dual core machine? There are no quad core Macbook Pros, only dual core with hyperthreading, meaning you have two physical cores, each of which can "split in half" to work on two threads for a total of four *logical* cores.

EDITED to add:

As for the red light, I found it would come on at random times even after being turned off so I just wrote a script to turn it off and then set up a CTRL-ALT-O hotkey in GNOME keyboard preferences that linked to that script. So any time I noticed the glowy red eye I could just hit that combo and kill it. 

Make a file with the following contents (I make ~/.bin/ directory for my scripts):

amixer set IEC958 off 

Then make the file executable:

chmod +x /path/to/script/script

Then assign a key combo in keyboard shortcuts to run that script. Keep in mind that the IEC958 is case sensitive.

Ah that explains it! Thanks! 

Also any idea about why I keep getting failed to update the sensors once in a while?

---

### Post by Rodimus Prime on 2010-10-17
Ugh I just had the Right Side update error pop up again! Twice in a row.

---

### Post by Rodimus Prime on 2010-10-17
So I did some more testing : 

I enabled disabled various sensors and different errors kept coming up. I took some screenshots.

[http://img143.imageshack.us/img143/4034/screenshotyrl.png](http://img143.imageshack.us/img143/4034/screenshotyrl.png)

[http://img233.imageshack.us/img233/2716/screenshot1jk.png](http://img233.imageshack.us/img233/2716/screenshot1jk.png)

[http://img689.imageshack.us/img689/2647/screenshot2ww.png](http://img689.imageshack.us/img689/2647/screenshot2ww.png)

---

### Post by Rodimus Prime on 2010-10-18
No one has any ideas as to why it is happening?

---

