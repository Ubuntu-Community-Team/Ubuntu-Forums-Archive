---
title: "Installing Swiftfox, which processor do I choose?"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by metalaxesucks on 2007-01-01
In the link below it tells me to choose a processor,
[http://www.getswiftfox.com/installer.htm](http://www.getswiftfox.com/installer.htm)
but I'm not sure which one I should choose.

My processor says
Intel Celeron Processor 2.20 GHz

The choices are:
Celeron (Willamette, Northwood, Celeron D)
Celeron M
Celeron (Coppermine, Tualatin)

Mine doesn't say any of these PARTICULAR ones
"Willamette, Northwood, Celeron D"
"M"
"Coppermine, Tualatin"

My Computer is an emachines model T2240, 40GB Hard Drive (partitioned in half with one side Windows and the other Ubuntu), Intel Celeron Processor 2.20 GHz, & 740 RAM

Thanks in advance

---

### Post by Lord Illidan on 2007-01-01
I believe yours is based on the Northwood architecture.

Try running /cat/proc/cpuinfo in the terminal for more info on your cpu. Post it here.

---

### Post by fatsheep on 2007-01-01
M would be the **M**obile processor (for laptops) so if your computer is a desktop then you can pretty safely rule out that choice.  I'm not sure about the other two choices though...

---

### Post by Stirling on 2007-01-01
I would try the one for "Celeron (Willamette, Northwood, Celeron D)"

---

### Post by metalaxesucks on 2007-01-01
> **Lord Illidan said:**
> I believe yours is based on the Northwood architecture.

Try running /cat/proc/cpuinfo in the terminal for more info on your cpu. Post it here.

I tried running /cat/proc/cpuinfo in the terminal and it said "no such file directory", sorry but I'm kinda new at this stuff - but anyways I copied and pasted the command you posted and it didn't work. I also tried putting "su" and "do" and "sudo" in front of your command and it still didn't work. I appreciate your patience, I'm still learning.
By the way, my computer is a desktop if that is any help.

---

### Post by blackmh on 2007-01-02
Its Celeron (Willamette, Northwood, Celeron D) for sure

---

### Post by towsonu2003 on 2007-01-02
> **metalaxesucks said:**
> I tried running /cat/proc/cpuinfo in the terminal and it said "no such file directory"

The command should have been
```

cat /proc/cpuinfo
```

---

### Post by metalaxesucks on 2007-01-02
> **towsonu2003 said:**
> The command should have been
```

cat /proc/cpuinfo
```

Thanks
I will take Mr/Ms blackmh's advice. He said:
"its Celeron (Willamette, Northwood, Celeron D) for sure"

---

### Post by ciscosurfer on 2007-01-02
You can also try these:
[LIST=1]
[*][http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox)
[*]For Firefox, you can try using Automatix2 or the script here: [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)[/LIST]

---

### Post by towsonu2003 on 2007-01-02
sorry, my bad. I posted without doing prior research... 

what's the output of 
```
sudo apt-get install x86info
x86info | grep -i model
```

it will give you the name you're looking for.

---

### Post by metalaxesucks on 2007-01-02
> **metalaxesucks said:**
> Thanks
I will take Mr/Ms blackmh's advice. He said:
"its Celeron (Willamette, Northwood, Celeron D) for sure"

Thanks

.

---

### Post by towsonu2003 on 2007-01-02
> **metalaxesucks said:**
> .

:-k

---

### Post by metalaxesucks on 2007-01-02
Thanks everybody
I got it working with Celeron (Willamette, Northwood, Celeron D)
Thanks again

---

### Post by Lord Illidan on 2007-01-02
Sry about that...was sleeping on the keyboard!

---

