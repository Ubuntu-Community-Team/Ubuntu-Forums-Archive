---
title: "Specs"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by IrishGangsta on 2006-07-12
Hey there,
Is there an easy way, other then rebooting 
to view the specs of my laptop.
i.e. The video driver, memory, harddrive capacity. etc...

---

### Post by tribaal on 2006-07-12
Dunno if that's what you're looking for, but there's a whole bunch of files in /proc that you can just "cat" to the screen to display lots of fun facts (like processor info, etc...).

Example: ```
cat /proc/cpuinfo
```

Hope this helps... enjoy :)

- trib'

---

### Post by IrishGangsta on 2006-07-12
that was kind of what i wanted.

Do u have anymore example codes to find out other facts about my laptop
Like memory and all of that

---

### Post by MrHorus on 2006-07-12
Yes - Linux follows the UNIX concept that "everything is a file" so is you get a listing of /proc you will see files representing everything in your computer.
```
ls /proc
```

You can then read these with less to see the information on them such as CPU specs, memory usage, IRQs etc.
```
less /proc/cpuinfo
```

Hope this helps

---

### Post by slimdog360 on 2006-07-12
you can see a few things in the system monitor. 
Also ,maybe you would like
```
sudo apt-get install gdesklets
```
I havent used it but Ive heard theres a few things in there which let you monitor temps, ram usage, things like that.

---

### Post by mcduck on 2006-07-12
'lspci' will give you fairly compplete list of devices in your machine.

Also, as well as 'cat /proc/cpuinfo', you can do 'cat /proc/meminfo' and that'll give you info about your memory (surprise!)

For disk capacity, try 'df -m' or 'df -h'

also, if you install & configure lm-sensors command 'sensors' will tell your sensor readings, like temperatures, voltages and fan speeds.

---

### Post by _simon_ on 2006-07-12
Applications -> Add / Remove (at the bottom) OR Synaptic

Type "Sysinfo" into the search box and install it.

You will then access it via Applications -> System Tools

Screenshot attached.

---

### Post by IrishGangsta on 2006-07-12
> **_simon_ said:**
> Applications -> Add / Remove (at the bottom) OR Synaptic

Type "Sysinfo" into the search box and install it.

You will then access it via Applications -> System Tools

Screenshot attached.


Thank You!

---

