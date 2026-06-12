---
title: "Ubuntu and batery life..."
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by ravi_s on 2007-11-02
I have a Fujitsu tablet which regularly gives me between 5.5 and 6 hrs running xXP. I installed Ubuntu a few days ago and have found that I'm now getting no more that 3.5 to 4 hrs max using the same screen brightness and default power settings. 
What's happening here? I can see that most of the time, the CPU's at 600Mhz (same as XP) but the laptop seems to be running hotter than with XP. Is this just the price to pay for running Ubuntu or is there some settings that I need to play with?
Any help would be greatly appreciated!

R.

---

### Post by swisscow on 2007-11-02
I think what you say about less battery with ubuntu than windows is generally true - it is from what I have read a common issue but getting better with each release. Read somewhere that this is an issue to be addressed in the next release (could be wrong - probably am)

---

### Post by Supergoo on 2007-11-02
Not to sure on this, but if you do a search of the posts here , I remember reading something about this, and someone said something about adjusting the power management settings. But I do not  know I kinda slow tonight. Just a question what version og Ubuntu are you using ?

---

### Post by ravi_s on 2007-11-02
The new one, 7.10.

Regards
R.

---

### Post by Joakim Stokland on 2007-11-02
> **Supergoo said:**
> Not to sure on this, but if you do a search of the posts here , I remember reading something about this, and someone said something about adjusting the power management settings. But I do not  know I kinda slow tonight. Just a question what version og Ubuntu are you using ?

In terminal:

```
sudo gconf-editor
```

Open the apps-section in the left hand menu. Scroll down to gnome-power-manager. Click cpufreq, and change policy_battery to "powersave".

Now your processor should slow down when mains are disconnected. This will make your battery last longer, and keep your laptop cooler.

Good luck!
Joakim

---

### Post by ravi_s on 2007-11-02
Excellent!
Thank you. I'll try it now!

R.

---

### Post by mridkash on 2007-11-03
Get a terminal application named powertop. It displays how much power your laptop is consuming and shows processes that consume most computing power. You can shut down those when not needed. It also suggests you how to save power while using battery. Ubuntu 7.10 has something called dynticks enabled in kernel that saves power during battery.

sudo apt-get install powertop

Edit: This utility is provided by Intel

---

### Post by ag65151 on 2007-11-03
powertool is a great tip.

Thanks.

---

