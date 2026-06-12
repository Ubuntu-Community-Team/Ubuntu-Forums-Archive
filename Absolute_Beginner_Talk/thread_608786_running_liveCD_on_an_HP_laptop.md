---
title: "running liveCD on an HP laptop"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by colomob on 2007-11-10
i been trying to run the live cd on my fairly new hp laptop. after booting the main ubuntu screen comes out but when i click run/install ubuntu  after checking the comands the screen goes black and nothing happens fatre that. whats happening??:mad:

---

### Post by mivo on 2007-11-10
In the Live CD menu, press F6. A line appears at the bottom. Here, replace "splash" with "nosplash" and remove "quiet". If it doesn't work outright, there will at least be an error message when you try to boot. :)

---

### Post by podunk on 2007-11-10
How fast did you burn your CD?

Try making a new install CD, this time burn it at the very slowest speed your writer will go.

---

### Post by colomob on 2007-11-10
i cange on the livecd menu to nonsplah and took out the quiet.....still the same thing happens..it goes to a dark screen after checking the comands...i also recreated a new cd and burn it with the lowest speed....still nothing happens...someone help please!:(

---

### Post by mivo on 2007-11-10
Did you use "nosplash"? (You wrote "nonsplash", with an extra "n", so I wanted to double-check. :))

---

### Post by lilkeith07 on 2007-11-10
I had the same problem on an HP laptop heres what I did.
When the menu screen comes up hit F6 and then at the end write "acpi=off noapic" without the quotes and thats what worked for me. Hope it helps!

---

### Post by cubeist on 2007-11-10
forget the nosplash stuff... that won't help booting.  The problem with live CD's and hp laptops is well known...  to boot from a live cd you may need to add one or more of these commands at your grub menu (hit e and add these to the end of the list)

noapic nolapic noirqpoll nosmp noapci

for the feisty cd I needed all of these... for the gutsy live cd I only need noapic... and be cautious with the last one noapci because if you don't have APM installed your fan may not work properly...

---

