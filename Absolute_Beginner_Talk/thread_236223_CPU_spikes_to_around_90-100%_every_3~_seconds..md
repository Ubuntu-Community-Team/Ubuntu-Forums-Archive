---
title: "CPU spikes to around 90-100% every 3~ seconds."
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by fate on 2006-08-14
I'm running an AMD64 3000+ with 1 gig of RAM, as well as a BFG Nvidia 6600GT running Twinview. (I'll gladly provide more system specs if requested.) I am **not** using the 64-bit edition of Ubuntu for the availability of programs purpose. By no means am I new to Linux as I've used several distros over the years, however, I find myself having a problem that I can't quite solve. I've posted this in the beginner's forum because maybe I'm just overlooking something, and perhaps this is a small, fixable issue.

No matter whether it's a new installation or not (as I've installed the available updates and nothing has solved the problem), a gdesklets CPU indicator reads that the CPU is spiking to above 70%-80% every three seconds. This happens even when the machine is idle, and the performance hit is clearly visible when I'm using the machine -- even the screensaver (currently GL) is pausing every three seconds in time with the mishap.

I've checked the X logs and have seen nothing drastic, and the system logs didn't reveal much in the way of problems either. As it usually works: Windows doesn't present this problem, nor did Ubuntu Breezy Badger. Mepis 3.4.3 also presented no problems like this.

Anyone have suggestions? I'll gladly take them at this point.

---

### Post by Rabreu on 2006-08-14
To find out wich application is consuming that amount of CPU, you can always open the system monitor ( System -> Administration -> System Monitor) and take a look at "% CPU" column.

---

### Post by fate on 2006-08-14
Thank you for replying, Rabreu.

I did check this, and the CPU indicator graph under the System Monitor confirmed everything the gdesklets CPU monitor confirmed -- a lag/spike every three seconds from a low percentage to 70% or higher. The running processes tab showed no outstanding CPU usage by any program at any time. I'm at a loss here.

---

### Post by Anduu on 2006-08-14
Open System Monitor and click on the processes tab.

Now click on the CPU column...this will order stuff according to cpu usage.

Now watch closely...every 3 seconds or so the offending process should pop to the top of the list.

---

### Post by WalmartSniperLX on 2006-08-15
yup pretty much said. I had the same prob

---

### Post by Anduu on 2006-08-15
Also got to View and check show all processes...

---

