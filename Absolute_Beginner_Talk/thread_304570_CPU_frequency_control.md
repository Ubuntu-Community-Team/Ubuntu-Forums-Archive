---
title: "CPU frequency control"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by Shuja on 2006-11-22
Ok I'm using VMware for a work project, that I have no problem with but I'm using my laptop to host a few of the VMs and the frequency scaling of the processor is causing some quirky time issues with them.  I don't want to remove the function but I do need a way to turn scaling on and off when needed.

---

### Post by Shuja on 2006-11-22
solved

---

### Post by adam.tropics on 2006-11-22
so share how!.....help the next bloke!

---

### Post by Shuja on 2006-11-22
```
sudo chmod +s /usr/bin/cpufreq-selector
```
It allows you to change the freq using the CPU Frequency Scaling Monitor applet in gnome.

[IMG]http://www.webanalysis.org/snapshot1.png[/IMG]

---

### Post by adam.tropics on 2006-11-22
Yes it does...another way to achieve the same is to do:

```

sudo dpkg-reconfigure gnome-applets
```
...for future reference. I don't think either is really any better though.

---

### Post by Azriphale on 2006-12-12
When you do 
sudo dpkg-reconfigure gnome-applets

a message comes up saying you can install the CPU-freq monitor with SUID.

This is exactly what
sudo chmod +s /usr/bin/cpufreq-selector
does. Thats what the +s means, so either way is exactly the same.

---

### Post by useResa on 2006-12-12
> **Shuja said:**
> ```
sudo chmod +s /usr/bin/cpufreq-selector
```It allows you to change the freq using the CPU Frequency Scaling Monitor applet in gnome.



Do I understand correctly that you can swith CPU Frequency Scaling on and off with this function?

Since the clocks in my VMs were running way to fast I have disabled the "Speedstep Enable" in the BIOS. The consequence of this is that the CPU frequency is no longer scaled but that always the max frequency is used.

If I understand correctly with your option I only have to set it to maximum if I run a VM and in all other cases can have my CPU Frequency Scaling working.

Could you please confirm this?

---

### Post by Azriphale on 2006-12-12
If I understand you correctly, then yes. By performing that instruction, you will be able to always set the CPU frequency yourself in Ubuntu (so you can set it to maximum when you want to run a VM), and when you shut down the VM, you can set it back to a stepping governor, so that it automatically scales down the speed if you are not doing anything.

---

### Post by useResa on 2006-12-12
> **Azriphale said:**
> If I understand you correctly, then yes. By performing that instruction, you will be able to always set the CPU frequency yourself in Ubuntu (so you can set it to maximum when you want to run a VM), and when you shut down the VM, you can set it back to a stepping governor, so that it automatically scales down the speed if you are not doing anything.

Thank you for explaining, this means I can set it back on and control it from my main OS.

---

### Post by wate on 2007-01-09
thank you for the solution.

---

### Post by robinlennox on 2007-05-13
How would I get the CPU frequency control next to my clock?

---

### Post by Wardo on 2007-10-31
Thank you for the solution!

---

