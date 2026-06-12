---
title: "Questions about sensors and sensors-applet"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by Prodromoi on 2008-01-18
I would like to have an easily viewable way of checking my hardware status - primarily temperatures and fan speeds without having to drop out of Linux and go into the BIOS.

I've installed lm-sensors and sensors-applet (I believe the latter is the GNOME sensors application).  However, I suspect I've missed out something important.

I don't see a menu entry for the sensors-applet package.  Entering "sensors-applet" in the terminal results in "command not found".  lm-sensors itself looks like it would need configuring since when I enter "sensors" in the terminal I get:

~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
              +3°C
Core0 Temp:
              -1°C
Core1 Temp:
              +2°C
Core1 Temp:
              -7°C

I'm running the standard GNOME desktop on 7.10.  What do I need to do to get an easy to refer to hardware monitor?  I don't need to run it all the time - just to be able to fire it up when I want to check the status.

Thanks in advance.

---

### Post by nalinde on 2008-01-18
never mind.. didn't read the post enough

---

### Post by Prodromoi on 2008-01-18
> **nalinde said:**
> never mind.. didn't read the post enough

It looks like conky has potential.  Not sure how to start/configure it though.  I've looked at the man pages and I'm rather lost.

When I run it from the terminal I just get this:
~$ conky
Conky: desktop window (10000ba) is subwindow of root window (328)
Conky: drawing to desktop window
Conky: drawing to single buffer

... and have to CTL-C to get the cursor back.

When I run it from a launcher (installing it doesn't create a menu entry) nothing seems to happen except that the conky process is listed as sleeping.

---

### Post by PmDematagoda on 2008-01-18
When you have installed the sensors-applet package, you can insert the applet to the GNOME deskbar by right-clicking on it, pressing Add to Panel and then selecting Hardware Sensors Applet in the list.

---

### Post by Prodromoi on 2008-01-18
Edit - scratch that - I've got the applet on the panel.  It's showing the same kind of temperatures as I listed above.  I just need to work out configuration now...

---

### Post by Prodromoi on 2008-01-18
OK... I've got the applet on the panel now - thank you.

It's displaying the four core temps that I got from entering "sensors" in the terminal, which at the moment are:
4 deg C, -2 C, 2 C, -8 C

... which I really suspect aren't even close to being accurate!

How do I calibrate or get the applet to display the correct temperatures?
How do I add fan speed display to the applet?

---

### Post by LeAstrale on 2008-01-18
ill just follow your thread here, it would be nice to have an easy look at the temperatures and so on :)

---

### Post by Prodromoi on 2008-01-18
Another step further...

Once you've installed lm-sensors and the sensors-applet, run the following command in the terminal
```
~$ sudo sensors-detect
```
... and answer yes to all the question that you will be asked.  Then restart your GUI or machine.

This enables additional sensors specific to your machine.  To add them to the applet display, right click the applet and select preferences.  On the sensors tab I have "libsensors" displayed; opening this up shows the list of valid sensors, which you can enable, re-order and rename as you desire.

But...  there's still some questions I have remaining.

Q1.  Why are my core temperatures reading so low?  I'm not using any kind of fancy liquid oxygen cooling - I certainly don't believe that they should be reading below zero!

Q2.  Can I send the GPU temperature as displayed in the nvidia-settings control panel to the applet for display?

Q3.  My "temp3" sensor is showing a constant +128 degrees C, which I also don't believe!  Any ideas about this?  (The entry from the command line version of sensors for this reads "*temp3:      +128°C  (low  =    +0°C, high =  +127°C)   sensor = disabled  * ".  Obviously I can simply choose to not display this, since the sensor is disabled - but what's causing it?  Where's it coming from?

---

### Post by NovaAesa on 2008-01-18
@Prodromoi - just curious, how are you getting your CPU to run so cold?

EDIT: Oops missed your last post.

---

### Post by PartisanEntity on 2008-01-18
Thread renamed upon request of OP

---

### Post by Prodromoi on 2008-01-18
> **NovaAesa said:**
> @Prodromoi - just curious, how are you getting your CPU to run so cold?

That's the thing... it's not running cold.  The real CPU temperature, as reported by the BIOS and by one of the temperature sensors in the applet is 39 degrees C.

The really cold core temperatures and the +128 C temperature are obviously wrong.  But why?  And what can I do about them?  (Apart from just hide them, which seems to be cheating!)

---

### Post by Prodromoi on 2008-01-18
Giving this post a bump so a new bunch of folks see it...

Has anyone else experienced the weird low core temperatures that my libsensors reckons I've got?  Or the bizarre +128 C temperature from wherever "temp3" is measured?  

Or generally... any ideas what's going on/wrong?

And does anyone know if it's possible to include the GPU temperature from nvidia-settings into the sensor-applet panel?

---

### Post by celticbhoy on 2008-01-18
[COLOR="SeaGreen"][SIZE="4"]Try this how-to :-

[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)[/SIZE][/COLOR]

---

### Post by Prodromoi on 2008-01-18
> **celticbhoy said:**
> [COLOR="SeaGreen"][SIZE="4"]Try this how-to :-

[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)[/SIZE][/COLOR]

Thanks, I looked through that earlier when trying to sort out the problem.  It doesn't seem to address the problems I've raised (not that I can find) - possibly since it's quite an old document.

---

### Post by celticbhoy on 2008-01-18
OK Prodromoi, I dont know to much on this subject as I have never felt the need to use these features, but I do have a copy Linux Format magazine, issue number 92 from may 2007. In this there is an article about this very subject. Having just had another scan through it I can give you this web address that may give you some answers 'www.lm-sensors.org'. If you cant get any further, I will scan the pages and e-mail them to you. It may give you some info or pointers to areas you have not tried yet.

---

### Post by Prodromoi on 2008-01-18
Much obliged - I spent a while on that website earlier too, but wasn't able to find the answers.  I'll PM you an e-mail address.

Thanks.

---

### Post by celticbhoy on 2008-01-18
OK just scanning the pages now.

---

### Post by darkknight209 on 2008-02-21
> **celticbhoy said:**
> OK just scanning the pages now.

Any luck on this subject?, After running sensors, i return with this 

johnpriest@serenity:~$ sensors -f
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +37°F
Core0 Temp:
             +32°F
Core1 Temp:
             +54°F
Core1 Temp:
             +46°F

it8716-isa-0290
Adapter: ISA adapter
VCore:     +1.14 V  (min =  +0.00 V, max =  +4.08 V)   
VDDR:      +1.20 V  (min =  +0.00 V, max =  +4.08 V)   
+3.3V:     +3.30 V  (min =  +0.00 V, max =  +4.08 V)   
+5V:       +5.03 V  (min =  +0.00 V, max =  +6.85 V)   
+12V:     +12.03 V  (min =  +0.00 V, max = +16.32 V)   
in5:       +3.15 V  (min =  +0.00 V, max =  +4.08 V)   
in6:       +1.86 V  (min =  +0.00 V, max =  +4.08 V)   
5VSB:      +5.03 V  (min =  +0.00 V, max =  +6.85 V)   
VBat:      +3.06 V
fan1:     1880 RPM  (min =    0 RPM)                   
fan2:        0 RPM  (min =    0 RPM)                   
fan3:        0 RPM  (min =    0 RPM)                   
temp1:       +52°F  (low  =  +261°F, high =  +212°F)   sensor = diode   
temp2:       +88°F  (low  =   +79°F, high =   +97°F)   sensor = thermistor   
temp3:      +262°F  (low  =  +261°F, high =  +212°F)   sensor = diode   
vid:      +1.100 V


now, temp 3 scares me to death, is something wrong??

---

### Post by celticbhoy on 2008-02-23
PM me an E-Mail address and I will send you the article, there is a section which covers readings which show for the wrong sensor.

---

### Post by chperry on 2008-04-19
I am having a similar problem with unrealistic temperatures.  I have a Dell T3400 with Dual Core processors.  I am getting temps of +13 to +18C for both.  I know this is not correct.  I would very much like to know the REAL temps.

---

### Post by celticbhoy on 2008-04-20
Again pm me an email address and i will send the article to see if it is any help

---

### Post by mannheim on 2008-05-09
> **chperry said:**
> I am having a similar problem with unrealistic temperatures.  I have a Dell T3400 with Dual Core processors.  I am getting temps of +13 to +18C for both.  I know this is not correct.  I would very much like to know the REAL temps.

I also have a Dell T3400. I am getting what looks like the correct temperatures reported for my four cores (under Ubuntu 8.04):

```

~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +31.0°C  (crit = +100.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +31.0°C  (crit = +100.0°C)                  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +30.0°C  (crit = +100.0°C)                  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +30.0°C  (crit = +100.0°C)           
```

Before getting this to work, I ran "sensors-detect" (I think) and followed the instructions there: in particular, I added the single line

```
coretemp
```

to the bottom of the file /etc/modules and rebooted. Is coretemp listed if you do a "lsmod"?

---

### Post by chperry on 2008-05-11
coretemp is there.  I get incorrect temps (lower than ambient).  I am running 7.10.  Perhaps an upgrade to Hardy will fix it.

---

### Post by lolwhites on 2008-05-12
Mine seemed to be OK in 7.10. Now I've upgraded to Hardy, temp2 reads 128C! That can't be right, can it?

---

### Post by noris2go on 2008-05-12
It seems like the new dual core athlon's need a compute line to average each of the two sensors per core and adjust with an offset. I found this:
[http://forums.suselinuxsupport.de/index.php?showtopic=59078](http://forums.suselinuxsupport.de/index.php?showtopic=59078)

There is something wrong though with lm-sensors 3 in Ubuntu 8.04
If you try to use a compute line like bellow to fix the k8 temp offsets it comes back with an error:

compute temp2 (((@+temp1)/2)+21) , (((@+temp1)/2)-21)
ignore temp1
label temp2 "CPU0 Temp"

The error is:
ERROR: Can't get value of subfeature temp2_input: No such subfeature known

---

