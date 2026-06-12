---
title: "Computer Shuting Down"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by guyarye on 2007-09-28
I use Ubuntu 7.04 with GeForce 2 and 1024 megabyte of RAM.
Sometimes my system is shutding down just like if I would shut it down from the button in the right up corner.

What do I need to upload for you to help me solve the problem ?

---

### Post by Arthur Archnix on 2007-09-28
1. Does it shut down and turn off, shut down and restart, or go into standby mode?

2. Does the auto-shutdown look any different from the manual shutdown (when you click the shutdown button)?

3. Does it happen regularly, and if so, does it happen if you leave the computer for a while?

Let's start with that.

---

### Post by guyarye on 2007-09-28
1. It shut down and turn off.
2.It looks the same.
3.It is shutting down without a reasonable explanation, and if I leave the computer for a while it may shut down after 10 min or after 10 days.

---

### Post by badguyanil on 2007-09-28
By shutdown i guess you mean it actually shows you the shutdown screen. Coz if it just stwitches off it may be a problem with the hardware and not just ubuntu!

---

### Post by nowshining on 2007-09-28
it may be that hibernation or standby is on, have u checked?

---

### Post by guyarye on 2007-09-28
What do you mean by hibernation or standby?
The computer is shutting down for no reason. What log do I need to upload for you to help me solve this problem?

---

### Post by Arwen on 2007-09-28
Are you sure your cpu fan is ok?Check out your cpu temp in bios,they are usually set to shut down the pc when cpu temperature is more than a specific number..

---

### Post by nowshining on 2007-09-28
system - preferences - power management

---

### Post by 3rdalbum on 2007-09-28
Linux is a more complex, newer operating system than Windows XP, so it uses more system resources. More system resources == more power usage and more heat. This could be exposing a previously undetected cooling or PSU fault, which is being triggered seemingly at random by Beagle indexing or something similar which uses a lot of system resources.  Your BIOS is probably sending an ACPI shutdown event to the operating system when your PSU flakes out or when your computer's temperature reaches critical.

To confirm if it's the system load that's the problem, try performing some activity which uses CPU power - for instance, ripping a DVD multiple times. Right-click the top Gnome panel, click "Add To Panel..." and scroll down until you find the "Sytem Monitor" applet. This will add a graph of CPU usage to the panel. If the graph is consistantly at 100% whenever your computer shuts down, then it's a hardware problem, most likely the cooling systems or the Power Supply Unit.

---

