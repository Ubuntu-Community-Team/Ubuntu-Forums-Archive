---
title: "CPU WPM temperature really high on system monitor"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by CryptiniteDemon on 2007-08-02
Okay, so I finally got some hardware monitoring software on ubuntu.  All my zones are fine coming in at around 100 degrees Fahrenheit.  But the sensor for cpu_wpm is showing up at 491 degrees F.  So is this at all normal?  I know that when I had windows, this was never one of the options to monitor, and this big read meter at the bottom of my screen is freaking me out.

---

### Post by shearn89 on 2007-08-03
isn't that like about 250 Celsius? (actually, its 255). I think it must be a mistake. As long as you're computer's working fine, i'd just turn that one off, or ignore it. Which specific software is it? Someone else might be able to help if its a software problem. You could also check it isn't actually that temp by shuttind down the computer and having a look inside - you'd notice if it was 255 degrees!

---

### Post by CryptiniteDemon on 2007-08-04
I'm guessing it's a mistake in the applet.  

It's that hardware sensor applet that you can put into the program tile.  

The thing is when I go through bash and use the sensors program everything comes out lookin' just fine, but on both my laptop and desktop there's always one sensor that rates ridiculously high for no  apparent reason when I view it through the applet.

I dunno.  My computer isn't on fire yet, so I'd say I'm safe.  The reason I was so worried is cause I just put in a new processor and I'm watching my temperatures like a hawk just in case I screwed something up.

---

### Post by shearn89 on 2007-08-04
I think its fine. As you said, its not in flames...

---

### Post by w4ett on 2007-08-04
Well, I have found that the lm-sensors does not read the temps or voltages correctly...they are off by a small amount...I double checked by use of the bios hardware monitor...voltages read lower than the actual -.6 volts and temp by 3-4 C high...when in doubt, always defer to the bios readings for your hardware..lm-sensors while good, isn't a perfect.

---

### Post by crypticmystic on 2007-08-07
If your sensor is working properly, it should *NEVER* be higher than 120 degrees Celsius.  Even Military spec chips are only good to an internal tempurature of 140C  or so..  

I suspect the monitor is not working properly if it says it's 200+C  .  At that temp the plastics on the case of the CPU itself will start to melt....  When you boot, go into the BIOS..  There is usually a area that lists the system stats, including CPU temp.. Which will be lower than normal on boot up (since not much is happening), but it probably shouldn't be higher than 60C or so...  That may give you a relative number to use with you current monitor...

---

### Post by crypticmystic on 2007-08-08
fwiw, I had to hack up /etc/sensors.conf to scale my tempurature to match what the bios was saying...

Specifically, for my machine noticed sensors said something :

    CPU Temp:    +30°C  (low  =    +6°C, high =   +56°C)   sensor = thermistor

And my bios said I was running at closer to 48C, so I looked for the "CPU Temp" and found the instance..

    label temp3       "CPU Temp"
    set   temp3_over  90
    set   temp3_low   10

I changed over and under temps to my desired targets, which are 90 and 10 and added this line afterwards to scale the temp and range...  so 30 -> 4.8 is a factor of 1.6...

    compute temp3  (1.6*@),((1.0/1.6)*@)

Now it's much closer to the real value:

    CPU Temp:    +48°C  (low  =   +10°C, high =   +90°C)   sensor = thermistor 

You will probably have to do some experimenting on your own..

PErsonally, I put "sensors -s ; sensors" in one xterm and emacs editing /etc/sensors.conf in the other.. with every change, rerun "sensors -s; sensors" and look at the results... hack away :)

Steve




CPU Temp:    +48°C  (low  =   +10°C, high =   +90°C)   sensor = thermistor

---

