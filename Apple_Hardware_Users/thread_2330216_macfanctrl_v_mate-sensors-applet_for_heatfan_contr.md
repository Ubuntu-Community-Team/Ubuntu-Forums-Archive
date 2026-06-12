---
title: "macfanctrl v mate-sensors-applet for heat/fan control ????"
date: 2016-07-09
forum: Apple Hardware Users
---

### Post by este.el.paz on 2016-07-09
I have MATE installed on a MBPro and I followed instructions posted here on setting up "macfanctrl" . . . but the fans seem to blow louder and more frequently even with it compared to OSX 10.9.  I recently saw a post on the U-MATE community about using "mate-sensors-applet" . . . so I looked through my applications and didn't see it.  I tried to launch it using the terminal and it said "command not found."  Then I searched it in synaptics and it showed that "mate-sensors-applet" was installed . . . is there any way to get this applet to show up?

Or, since I have macfancntrl set up already that prevents the "mate-sensor-applet" from showing up?  It does seem like "heat" is an issue for intel Macs, and I have a MP that I'd like to get MATE installed on, and get it set up to handle the fans such that it is efficient, but simple???

e...

---

### Post by awjrichards on 2016-08-20
What does your /etc/macfanctl.conf look like? I'm not sure about the applet issue (I've never used Mate), but I found the default macfanctl settings to be too aggressive for my MacBook Air 6,2 (fans kicking on way more often than necessary - too noisy, too much power consumption).

I copied [someone else's example]("http://lesavik.net/post/getting-ubuntu-linux-to-work-on-macbook-air-7.2/") that they use for their MacBook Air 7,2 and have been happy with it:
```

# Config file for macfanctl daemon
#
# Note: 0 < temp_X_floor < temp_X_ceiling
#       0 < fan_min < 6200       

fan_min: 1000

temp_avg_floor: 45
temp_avg_ceiling: 55

temp_TC0P_floor: 52
temp_TC0P_ceiling: 60

temp_TG0P_floor: 50
temp_TG0P_ceiling: 58

# Add sensors to be excluded here, separated by space, i.e.
# exclude: 1 7
# will disable reading of sensors temp1_input and temp7_input.

exclude: 18 19

# log_level values:
#   0: Startup / Exit logging only
#   1: Basic temp / fan logging
#   2: Log all sensors  

log_level: 0

```

Also, what version of MacBook Pro do you have and which CPU? With a quick Google search you can figure out the maximum safe operating temperature for the CPU and adjust macfnctrl.conf accordingly.

---

### Post by awjrichards on 2016-08-20
What does your /etc/macfanctl.conf look like? I'm not sure about the applet issue (I've never used Mate), but I found the default macfanctl settings to be too aggressive for my MacBook Air 6,2 (fans kicking on way more often than necessary - too noisy, too much power consumption).

I copied [someone else's example]("http://lesavik.net/post/getting-ubuntu-linux-to-work-on-macbook-air-7.2/") that they use for their MacBook Air 7,2 and have been happy with it:
```

# Config file for macfanctl daemon
#
# Note: 0 < temp_X_floor < temp_X_ceiling
#       0 < fan_min < 6200       

fan_min: 1000

temp_avg_floor: 45
temp_avg_ceiling: 55

temp_TC0P_floor: 52
temp_TC0P_ceiling: 60

temp_TG0P_floor: 50
temp_TG0P_ceiling: 58

# Add sensors to be excluded here, separated by space, i.e.
# exclude: 1 7
# will disable reading of sensors temp1_input and temp7_input.

exclude: 18 19

# log_level values:
#   0: Startup / Exit logging only
#   1: Basic temp / fan logging
#   2: Log all sensors  

log_level: 0

```

Also, what version of MacBook Pro do you have and which CPU? With a quick Google search you can figure out the maximum safe operating temperature for the CPU and adjust macfnctrl.conf accordingly.

---

### Post by este.el.paz on 2016-08-20
@awjrichards:

Thanks for the post . . . I'm away from that MBPro right now, it's an "09" model purchased in '10 . . . 5,1??  But, I do appreciate posting the macfanctl params that you are using . . . at the time, a year or two back when I was fiddling with it I couldn't find "recommended temps" for OSX, even posting on the Apple Community forum to try to get some data . . . didn't seem to get too much feedback.

I did go through the "delete the highs and lows" on the various sensors . . . and that did cut back on the use of the fan, a bit . . . but . . . when I get back to the MBPro and booted up in LM, maybe I'll check your suggestions and see what happens . . . try to post back, etc.

e..

---

### Post by awjrichards on 2016-08-20
Cool - the CPUs in all of the 2009 MacBook Pro models have a max temp of 105C, at least according to notebookcheck.net :)

---

