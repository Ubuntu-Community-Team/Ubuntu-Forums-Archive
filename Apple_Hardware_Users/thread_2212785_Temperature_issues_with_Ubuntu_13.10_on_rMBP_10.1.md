---
title: "Temperature issues with Ubuntu 13.10 on rMBP 10.1"
date: 2014-03-23
forum: Apple Hardware Users
---

### Post by Aybara on 2014-03-23
I installed 13.10 on my rMBP 10.1. The install went well, it looks beautiful, and it overheats :)

I installed rEFInd with "./install.sh --alldrivers". From the Live Stick I started the installer with "ubiquity -b" to install without a bootloader. I chose "Install alongside OSX" and installed. Everything looked good, but after a while the logs started filling up with "Package temperature above threshold, cpu clock throttled".

I know little about BIOS/EFI/UEFI, but from googling it seems it can be relevant, maybe because of NVIDIA drivers? I had dual boot before the latest OSX upgrade broke it. That was Ubuntu 13.04 with Grub, and I didn't have any heat issues then.

---

### Post by andy10 on 2014-03-23
I used the "control" script in a cron task referenced in this article on my mid 2012 MacBook Pro and it took care of my fan/heat issues.

[http://unencumberedbyfacts.com/2013/08/16/linux-on-a-macbook-pro-101/](http://unencumberedbyfacts.com/2013/08/16/linux-on-a-macbook-pro-101/)

Andy

---

### Post by Aybara on 2014-03-25
That looks promising. Thanks.

---

### Post by PartisanEntity on 2014-03-25
You can try this advice: [http://ubuntuforums.org/showthread.php?t=2156916&p=12741552#post12741552](http://ubuntuforums.org/showthread.php?t=2156916&p=12741552#post12741552) 

It works for me on my iMac. I am using the "mid" profile.

---

### Post by MikeBraxner on 2014-03-28
Perin --- 

I can't tell from your original posting if your trouble is with the MBPr running to hot, or with mis-adjusted fan settings ... clarification would be helpful.

If  you are ***sure*** it's the former, I would suggest trying a different kernel and, if you actually use the NVidia, a different proprietary driver, that usually settles things done quick. 

If it's the latter, make sure you have access to Mactel's 'Support for Linux on Apple Machines' (*sudo add-apt-repository ppa:mactel-support/ppa*), and install **applesmc,** **lm-sensors** and **macfanctld**.

Start up **applesmc** (*sudo modprobe applesmc*) and install **lm-sensors** for easier access and monitoring of sensors, and **coretemp** to allow lm_sensors access to specific sensors, the rotation speed of the fan, and the GPU temperature (just clip coretemp to the end of /etc/modules and start it up) ...

```
sudo tee -a /etc/modules <<-EOF
    coretemp
EOF

sudo modprobe coretemp 

```

Once installed, have a look at the actual temperature readings (*watch sensors*), which should narrow/focus your concern.

Finally, get **macfanctld** to handle the fan adjustments automatically, using a more conservative configuration file as a baseline ... 

```
[COLOR=#000000][FONT=Ubuntu Mono]# Config file for macfanctl daemon
# Location:  [/FONT][/COLOR][COLOR=#000000]/etc/macfanctld.conf[/COLOR][COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]#
# Note: 0 < temp_X_floor < temp_X_ceiling
#       0 < fan_min < 6200       

fan_min: 2000

temp_avg_floor: 45
temp_avg_ceiling: 50

temp_TC0P_floor: 45
temp_TC0P_ceiling: 52

temp_TG0P_floor: 50
temp_TG0P_ceiling: 58

# Add sensors to be excluded here, separated by space, i.e.
# exclude: 1 7
# will disable reading of sensors temp1_input and temp7_input.

exclude: 13 17 18 19 25 32 33 34 35


# log_level values:
#   0: Startup / Exit logging only
#   1: Basic temp / fan logging
#   2: Log all sensors  

 [COLOR=#000000][FONT=Ubuntu Mono]log_level: 0[/FONT][/COLOR]
```

Since macfanctld uses in part summarized averages to control the fans (see *man macfanctld*) you should exclude all sensors that report bogus readings. For a quick peek, try *macfanctld -f*, note the malefactors in the sensor lot, and amend the 'exclude' line accordingly. Pay particular attention to the NVidia related ones ... if you disabled the NVidia, then those readings come in as "-127" which really screws macfanctld's averages, and thus, inhibits the fans. If you don't like my trigger values for fan speed, or temperatures, set your own. Then a final *service macfanctld start* and you should be set.


If you want to keep an eye on the temps and fans' rpm for a while, set "log_level : 1", stop and restart macfanctld, and periodically check /var/log/macfanctld.log until you're satisfied, then reset the log_level.

Hope this helped

PS: Just to clarify, the exclude line in the above config file for macfanctld is set for a configuration **without** NVidia, i.e. i915 only. If you use the NVidia card, remember to re-enable the appropriate sensors (TG1D,TG1F,TG1d) by removing their ids from the exclude list (17,18,19), leaving you with 'exclude: 13 25 32 33 34 35'. If you're unsure, check if you get any sensible readings (i.e. NOT -127.0°C) for those three via *watch sensors*, and confirm their status with *macfanctld -f.*

---

### Post by este.el.paz on 2014-05-07
> **MikeBraxner said:**
> Perin --- 

I can't tell from your original posting if your trouble is with the MBPr running to hot, or with mis-adjusted fan settings ... clarification would be helpful.
If it's the latter, make sure you have access to Mactel's 'Support for Linux on Apple Machines' (*sudo add-apt-repository ppa:mactel-support/ppa*), and install **applesmc,** **lm-sensors** and **macfanctld**.
Start up **applesmc** (*sudo modprobe applesmc*) and install **lm-sensors** for easier access and monitoring of sensors, and **coretemp** to allow lm_sensors access to specific sensors, the rotation speed of the fan, and the GPU temperature (just clip coretemp to the end of /etc/modules and start it up) ...
```
sudo tee -a /etc/modules <<-EOF
    coretemp
EOF
sudo modprobe coretemp 

```
Once installed, have a look at the actual temperature readings (*watch sensors*), which should narrow/focus your concern.
Finally, get **macfanctld** to handle the fan adjustments automatically, using a more conservative configuration file as a baseline ... 
If you're unsure, check if you get any sensible readings (i.e. NOT -127.0°C) for those three via *watch sensors*, and confirm their status with *macfanctld -f.*

@MikeB:

I've posted a few threads here on the apple user forum in the last few months looking into the heat issues with linux on mac . . . and you may have replied to one of them, but, I couldn't find "macfanctld" before yesterday . . . after a long afternoon of reading I found the "swedish wings" posts from the dev? of macfanctld . . . and then on to the "mactel ppa" . . . in going there I saw that there are different versions for different upgrades of ubuntu . . . but none for "trusty" . . . .  

Just wondering if you are or know the swedish wings person . . . or if you know whether there would be a need for the trusty update to get the heat issue under control in my '10 MBPro . . . running trusty Xu/MATE 64 bit??  Is it critical to get the updated macfanctld for the specific version?  Or, really it's all the same?

If you, or if you know someone, who knows about whether macfanctld will be updated soon for trusty, I'm about ready to try and acquire it . . . it seems like 14 is actually running warmer than LM16 on my computer . . . my thread:

[http://ubuntuforums.org/showthread.php?t=2222611](http://ubuntuforums.org/showthread.php?t=2222611)

e.e.p.

---

