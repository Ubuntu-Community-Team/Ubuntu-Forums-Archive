---
title: "manage cpu frequency of 1215N (how to)"
date: 2011-08-27
forum: Asus Ubuntu Support (CLOSED)
---

### Post by AmiNimA on 2011-08-27
[COLOR=Black]to manage cpu frequency of the 1215N, do as follow with root:

[/COLOR][COLOR=Black]sudo apt-get install cpufrequtils sysfsutils

sudo modprobe [/COLOR][COLOR=Black][COLOR=#FF0000][COLOR=Black]p4_clockmod[/COLOR]

[/COLOR]sudo modprobe cpufreq_ondemand

sudo echo ondemand | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
sudo echo ondemand | sudo tee /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

sudo echo [/COLOR][COLOR=Black][COLOR=#FF0000]p4_clockmod[/COLOR] | sudo tee -a /etc/modules
sudo echo cpufreq_ondemand | sudo tee -a /etc/modules

sudo gedit[COLOR=#FF0000][COLOR=Black]/etc/sysfs.conf

[/COLOR][COLOR=Black]then add this lines and save:[/COLOR]
[/COLOR]devices/system/cpu/cpu0/cpufreq/scaling_governor = ondemand
devices/system/cpu/cpu1/cpufreq/scaling_governor = ondemand

thanks to [[+]("http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html")]
----------------------------------------------------------------

ok, reboot. now you can change the cpu frequency by the cpufreq applet. but I have a problem in setting the governors to for example conservative. it always stays at performance.
any idea?
[/COLOR][COLOR=Black]
[/COLOR]

---

### Post by chilloutmo on 2011-12-16
Hello,

I did the above and it kind of screwed up cpu scaling. I used this because I was annoyed by what I was considering a too active fan. However, I already had jupiter installed and now I think it broke a good functioning of jupiter. I removed the two lines again with gedit and also uninstalled the cpu frequtils, I uninstalled jupiter and re-installed it but the problem persists.  

Concretely, with jupiter the power saving mode does not longer work correctly, as it slows down the computer so much that I can't do anything, which was obviously not the case before. So I have to always run in max performance mode, or as I am doing it now, with no jupiter at all, but that is not satisfactory as well, as battery life and cpu temperature both suffer. 

I used to be able to work normally in power saver mode with jupiter which is something I would like to get back. Since the problem started with the implementation of the above instructions, I wanted to ask you if anybody of you could help me reverse what I did or help me solve my problem in any other way. 

Thanks!

---

### Post by AmiNimA on 2011-12-17
> **chilloutmo said:**
> 

I used this because I was annoyed by what I was considering a too active fan. 


this is nvidia ION, not CPU. disable nvidia to reduce fan speed. by disabling nvidia and its fan battery will increase 1 more hour. there is a topic in this forum about it.

hmmm, I haven't tried jupiter and I wont try ubuntu anymore, so I cannot help you solve your problem. sorry my friend... but if you do a fresh install, you must not have any problem. it's a little odd you said even after a fresh install your problem did not solve.
try to format your linux partition and install annother version of ubuntu, or annother distro, (i.e [parsix]("http://parsix.org"), fedora, suse...) so you could find if there is a software problem or hardware?

---

