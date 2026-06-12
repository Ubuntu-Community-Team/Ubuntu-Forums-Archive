---
title: "Back after three years, some questions"
date: 2010-11-19
forum: Apple Hardware Users
---

### Post by dpny on 2010-11-19
With my new Mac Pro as my main machine I have installed Ubuntu 10.10 on my G5, and have two quick questions.

1) The machine had an X800XT in it, but the Live CD would give me a white screen after attempting to boot. I put an nVidia 5200 in, and it works fine. However, I would like to put the X800 back in, so I can play with Compiz. Thing is, seems like Ubuntu doesn't have an xorg.conf file to alter any more. Can I generate one and use it anyway?

2) Last time I had Ubuntu installed, there was no way to get temperature and fan data from PPC machines. Is this still the case? I have played around with lm-sensors, but haven't had any luck.

---

### Post by endotherm on 2010-11-19
if you put an xorg.conf in /etc/X11/ it will be used, but by default, X doesn't store config info any more, but instead generates its config and applies settings from apps like the System -> Preferences -> Monitors applet, or the xRandR cli app.   
I am not a mac person, so I'm afraid I can't help you with lmsensors, other than to advise you to rerun 'sensors-detect' and answer yes to everything. then check 'sudo sensors' again.

---

### Post by dpny on 2010-11-19
Is there a way to generate an xorg.conf file, or are there samples I can use?

---

### Post by shawnhcorey on 2010-11-19
For tempature, try reading: ```
/proc/acpi/thermal_zone/THRM/temperature
```

---

### Post by endotherm on 2010-11-19
depending on the driver you have, you may have an application called 
'nvidia-xconfig'
it will generate a base xorg.conf for your nvidia based system. not sure if the utility is installed with teh driver you are using though.

if so, run it like
```
sudo nvidia-xconfig
```

---

### Post by dpny on 2010-11-19
> **endotherm said:**
> depending on the driver you have, you may have an application called 
'nvidia-xconfig'
it will generate a base xorg.conf for your nvidia based system. not sure if the utility is installed with teh driver you are using though.

if so, run it like
```
sudo nvidia-xconfig
```

Thanks. Will give it a try. So long as I can generate a .conf file I can modify it by hand.

---

### Post by dpny on 2010-11-22
sudo nvidia-* does nothing. I searched the software downloader and couldn't find anything with "nvidia" in the title which didn't look like an additional driver.

After some googling I tried sudo Xorg -configure, but I got a message that the X server was in use, and I couldn't stop it. Ctrl-Alt-F1 doesn't do anything, and neither did any other key combo I tried.

I then tried sudo dpkg-reconfigure xserver-xorg, but far as I can tell that doesn't do anything.

The symptoms are: after booting, the screen goes white, with some garbled lines of color at the top, and the fans steadily spin up to max.

Can I boot into a command line mode?

---

### Post by dpny on 2010-11-22
Is anyone successfully using 10.10 with a G5 and an ATi X800XT? Can it even be done?

---

