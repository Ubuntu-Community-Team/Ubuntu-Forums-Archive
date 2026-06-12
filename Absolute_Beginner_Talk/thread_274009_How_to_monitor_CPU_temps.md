---
title: "How to monitor CPU temps?"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by TwistedTripper on 2006-10-09
Hi Everyone

I would like to monitor my CPU temps and am a tad lost (just joined the Ubuntu folding team so I'm curious about my CPU temps running under 100% load). I think lmsensors can help me but haven't a clue as to what I'm doing...total N00B to Ubuntu or Linux for that matter, been running Ubuntu 6.06 for a couple of weeks now :)

I've managed to install lmsensors but when it comes to configuring it I get overwhelmed at this point;

I will now generate the commands needed to load the I2C modules.
 Sometimes, a chip is available both through the ISA bus and an I2C bus.
 ISA bus access is faster, but you need to load an additional driver module
 for it. If you have the choice, do you want to use the ISA bus or the
 I2C/SMBus (ISA/smbus)? isa

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA I2C Device
# modprobe unknown adapter NVIDIA I2C Device
# modprobe unknown adapter NVIDIA I2C Device
i2c-isa
# I2C chip drivers
eeprom
w83627ehf
#----cut here----

Do you want to add these lines to /etc/modules automatically? (yes/NO)no

Can anyone give me some direction in setting this thing up?

---

### Post by zappa on 2006-10-09
I think it will be much easier to just right-click your panel and add system monitor. With a right-click on it you can further customize it.

---

### Post by Kateikyoushi on 2006-10-09
I use the gnome cpufreq applet which I only had to install and shows the correct tempreture on my panel. It is part of the gnome-applets package.

You can install it via synaptic, or from terminal with the following commands.

```
sudo aptitute update
sudo aptitue install gnome-applets
```

---

### Post by TwistedTripper on 2006-10-09
Thanks Zappa

That's a neat trick (learn something new every minute...cool) but unfortunately system monitor doesn't tell me the temperature of my CPU.

Cheers

Kateikyoushi, I sorta installed KDE so don't know if it will work?

Thanks

---

### Post by Kateikyoushi on 2006-10-09
That won't work under KDE because that's a gnome applet but you could try emifreq.

---

### Post by wjp.reg on 2006-10-09
I've been monitoring cpu temp on my laptop using the gnome sensors applet.  Works for me :)

---

### Post by TwistedTripper on 2006-10-09
> **Kateikyoushi said:**
> you could try emifreq.


No go. Interesting that it only shows my frequency at 1.0GHz (45%) when my processor is a AMD 3500 venice, which should be running at 2.2GHz. Checked my BIOS and it's running at 2.2 so all is good. Temp in bios is 31 deg c but still would like to know how hot it gets at 100% load.

What happens if I install the other gnome sensors applet, will it stuff up the OS or just not work?

---

### Post by daemonoid on 2006-10-09
take a look at this:

[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

It's pretty much the method i used to get it all set up, give us a shout if you have any more problems, i'll try to assist - it's been a while since i last got this working.

---

### Post by TwistedTripper on 2006-10-09
Cheers daemonoid

Think that was the guide I was following and I got to the point where I ran the sensors-detect, however got stumped with the question; 
"Do you want to add these lines to /etc/modules automatically? (yes/NO)no" 

I got confused with whether I ought to let it do it automatically or if I had to modify the /etc/modules thing manually, I recall it saying to generally pick the defaults at the start, which seemed to be answer No. Not very confident, I don't have any real idea what it's about.

Anyway, thanks everyone for your help. Much appreciated. It's getting late here in Sydney so best if I take a break and re-visit it tomorrow b4 I mess things up.

;)

---

### Post by hcgtv on 2006-10-09
GKrellM is the best I've every used:
[http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html](http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html)

There should be a deb for it in the repository.

---

### Post by TwistedTripper on 2006-10-10
> **TwistedTripper said:**
> 
To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA I2C Device
# modprobe unknown adapter NVIDIA I2C Device
# modprobe unknown adapter NVIDIA I2C Device
i2c-isa
# I2C chip drivers
eeprom
w83627ehf
#----cut here----

Do you want to add these lines to /etc/modules automatically? (yes/NO)no


Got it to work :) Woo Hoo!

Where I went wrong is answering no to the last question. So I took a punt and answered yes to add the lines automatically. Rebooted and presto! I now have a monitor for my CPU temp...after all what did I have to lose? Reinstall maybe? But what the hey..its not like I don't have to reinstall windows every few months when I manage to stuff that up hehehe. Had no idea what I was doing but my system seems to be functioning okay.

Also installed GKrellM. Thanks hcgtv.

The only down side is that I don't believe the sensor is correct LOL. 28.5 deg c is a little low IMO. But that's beside the point.

Cheers everyone

---

### Post by daemonoid on 2006-10-11
I rarely listen to defaults if the other option seems easier ;)

---

