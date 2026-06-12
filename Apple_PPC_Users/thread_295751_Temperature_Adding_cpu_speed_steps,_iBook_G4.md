---
title: "Temperature: Adding cpu speed steps, iBook G4 ?"
date: 2006-11-08
forum: Apple PPC Users
---

### Post by bogoliubov on 2006-11-08
Hello, I run Edgy on my iBook G4 and I am almost happy with how the computer behaves.

But the fans are annoying! So my question is if the G4 CPU in the iBook can use more than two steps in the cpufreq scaling!? Now it jumps from 600 to 1200 MHz, and I suspect that this is not optimal...


Also, how do I tweak the therm_adt746x settings? Now I have (in /etc/modules)
therm_adt746x fan_speed=100 limit_adjust=-5

I've tried setting fan_speed=1, but this doesn't help much. I'd like the fans to start at low temps but slowly, and have it so that the fan don's scale so aggressively with increasing temp. Is this possible somehow? What about the sensor2 setting?

And a powersaving-related issue: I can't get my iBook to sleep when closing the lid. This worked in Dapper!

---

### Post by mr_forest on 2006-11-08
hello, bogoliubov.
1) afaik, cpu freq scaling can only switch between these, because  actually the cpu can work only at these frequencies. it's a clockfreq matter, i think.
try "cat /proc/cpuinfo" for more infos.
2) try to manage temps and sensors with sensors-applet, for me it worked (kind of),with little control on the fan anyway..
3) the sleep on lid close works for me.. did you set up power manager?

---

### Post by bogoliubov on 2006-11-09
> **mr_forest said:**
> 
3) the sleep on lid close works for me.. did you set up power manager?

Thanks for the help. I installted pbbuttonsd/powerprefs and then I did
sudo powerprefs
Then I edited the AC and Battery profiles, I choosed "suspend to disk" as "On conver action". This didn't do it, but neither did "suspend to ram"...

Any ideas?

---

### Post by engla on 2006-11-10
Try gnome-power-manager first -- it works on my ibook (bought feb 2005). gnome-power-manager is the little battery in your notification area (perhaps only shows when you're running on battery). You should be able to set its action-on-close, and choose suspend to ram. I have never seen suspend-to-disk (hibernate) work with linux on this ibook (works in os x though).

---

### Post by bogoliubov on 2006-11-12
> **engla said:**
> Try gnome-power-manager first -- it works on my ibook (bought feb 2005). gnome-power-manager is the little battery in your notification area (perhaps only shows when you're running on battery). You should be able to set its action-on-close, and choose suspend to ram. I have never seen suspend-to-disk (hibernate) work with linux on this ibook (works in os x though).

Thanks, that did the trick!

---

