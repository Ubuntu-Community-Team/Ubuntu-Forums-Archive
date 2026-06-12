---
title: "CPU frequency scaling un-supported"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by delilahjed44 on 2007-04-05
[COLOR="DarkRed"]Hey Tecks.  I am receiving the error CPU Frequency Scaling un-supprted.  I checked for the color, it is working at 100% then opened up monitor properties and saw that the cpufreq-applet is sleeping.  But this sign pops up now everytime I open Ubuntu 6.10 edgy eft.  I looked through the archives and read, but did not see one that pertained to Ubuntu.  Thank you.

Sherri[/COLOR]

---

### Post by teaker1s on 2007-04-05
I'm guessing that the modules are not loaded, while no expert on this-what cpu do you have?

---

### Post by serag on 2007-04-05
either your cpu doesn't support it, or you have acpi disabled (usually need to boot some types of laptops/pc's)

---

### Post by teaker1s on 2007-04-05
err no example my system installed powernowd and got same error, you could of course try
```
gksudo synaptic
``` and search frequency scaling and try an alternative to installed package and see if it works.
also possible I had to do below

PowerNow amd 64
In order to take advantage of the various CPU clock states of the laptop, you should apt-get install powernowd and make sure that the frequency scaling and powernow modules are loaded in /etc/modules:
# CPU frequency
freq_table
cpufreq_userspace
# powernow
powernow-k8

---

### Post by delilahjed44 on 2007-04-05
[COLOR="DarkRed"]Heyyyyy, thanks for the help, now are you thinking this is a laptop? it is not.  Not sure how to find the CPU for you, and not sure exactly if you want all this listed to be downloaded from synaptic. I am going to write this down and look.

Sherri[/COLOR]

---

### Post by delilahjed44 on 2007-04-05
Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

This is what I get when I do the apt-get-install powernowd ??

Sherri

---

### Post by delilahjed44 on 2007-04-05
[COLOR="DarkRed"]AAAAAAHHHHHH its me again, this is what I found on monitor Freguency scaling monitor 2.16.1 How do I know what modules to download and are they in synaptic? separate or in package deal??

Thanks, wheww its almost Friday....[/COLOR]

---

### Post by teaker1s on 2007-04-05
howto explanation of powernowd
[http://ubuntuforums.org/showthread.php?t=248867&highlight=powernowd]("http://ubuntuforums.org/showthread.php?t=248867&highlight=powernowd")

modules are often in the kernel and are turned on as required, the link above is your best choice

---

### Post by delilahjed44 on 2007-04-05
[COLOR="DarkRed"]Hello, well you did not say which to follow so I am guessing at it all.  I did the first 3 steps that is all.  Nothing else looked famliar to me.

Sherri thanks. guess I will see[/COLOR]

---

### Post by delilahjed44 on 2007-04-05
> **teaker1s said:**
> I'm guessing that the modules are not loaded, while no expert on this-what cpu do you have?

[COLOR="DarkRed"]Hey I have a pentium 4 processor and I am running ubuntu edgy eft.  

Sherri[/COLOR]

---

### Post by chalex on 2007-04-05
The easiest way to find out more about your processor is to type ```
cat /proc/cpuinfo
```

To find out more about frequency scaling: ```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies

```

In any case, the message is harmless, it merely means your processor doesn't have the frequency scaling feature.

---

