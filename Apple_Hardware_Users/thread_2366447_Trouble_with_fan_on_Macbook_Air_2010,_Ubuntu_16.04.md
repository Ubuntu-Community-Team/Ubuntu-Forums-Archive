---
title: "Trouble with fan on Macbook Air 2010, Ubuntu 16.04"
date: 2017-07-17
forum: Apple Hardware Users
---

### Post by digital-larry on 2017-07-17
We have managed to install macfanctld, and it gives the following output.

```
martin@LinuxBookAir:~$ cat /var/log/macfanctl.log 
Using parameters:
    temp_avg_floor: 45
    temp_avg_ceiling: 55
    temp_TC0P_floor: 50
    temp_TC0P_ceiling: 58
    temp_TG0P_floor: 50
    temp_TG0P_ceiling: 58
    fan_min: 2000
    log_level: 1
Found applesmc at /sys/devices/platform/applesmc.768
Found 1 fan.
Found 26 sensors:
     1: TB0T - Battery TS_MAX Temp 
     2: TB1T - Battery TS1 Temp 
     3: TB2T - Battery TS2 Temp 
     4: TC0D - CPU 0 Die Temp 
     5: TC0E - ? 
     6: TC0P - CPU 0 Proximity Temp 
     7: TC1E - ? 
     8: TCZ3 - ? 
     9: TCZ4 - ? 
    10: TCZ5 - ? 
    11: TG0E - ? 
    12: TG1E - ? 
    13: TG2E - ? 
    14: TGZ3 - ? 
    15: TGZ4 - ? 
    16: TGZ5 - ? 
    17: TH0F - ? 
    18: TH0O - ? 
    19: TM0P - ? 
    20: TN0D - MCP Die 
    21: TN0P - MCP Proximity 
    22: TN1D - ? 
    23: Th1H - ? 
    24: Tp0P - ? 
    25: Ts0P - Palm Rest Temp 
    26: Ts0S - ? 
Speed: 6200,  AVG: 43.4C, *TC0P: 63.5C
Speed: 6200,  AVG: 43.6C, *TC0P: 64.2C
Speed: 6200,  AVG: 43.8C, *TC0P: 64.8C
Speed: 6200,  AVG: 43.8C, *TC0P: 65.0C
Speed: 6200,  AVG: 44.4C, *TC0P: 65.2C
Speed: 6200,  AVG: 45.0C, *TC0P: 66.2C
Speed: 6200,  AVG: 45.2C, *TC0P: 66.8C
Speed: 6200,  AVG: 45.2C, *TC0P: 67.2C
Speed: 6200,  AVG: 44.8C, *TC0P: 66.8C
Speed: 6200,  AVG: 44.8C, *TC0P: 66.8C
Speed: 6200,  AVG: 44.8C, *TC0P: 66.5C
Speed: 6200,  AVG: 44.6C, *TC0P: 66.5C
Speed: 6200,  AVG: 44.5C, *TC0P: 66.5C
Speed: 6200,  AVG: 44.4C, *TC0P: 66.2C
Speed: 6200,  AVG: 44.2C, *TC0P: 66.0C
Speed: 6200,  AVG: 44.2C, *TC0P: 65.8C
Speed: 6200,  AVG: 44.1C, *TC0P: 65.8C
Speed: 6200,  AVG: 44.2C, *TC0P: 65.8C
Speed: 6200,  AVG: 44.3C, *TC0P: 66.0C
Speed: 6200,  AVG: 44.4C, *TC0P: 66.0C
Speed: 6200,  AVG: 44.3C, *TC0P: 65.8C
Speed: 6200,  AVG: 44.2C, *TC0P: 65.8C
Speed: 6200,  AVG: 44.1C, *TC0P: 65.5C
Speed: 6200,  AVG: 44.0C, *TC0P: 65.5C
Speed: 6200,  AVG: 43.9C, *TC0P: 65.2C
Speed: 6200,  AVG: 43.9C, *TC0P: 65.2C
Speed: 6200,  AVG: 43.8C, *TC0P: 65.2C

```

Speed is always 6200 and it does not appear that the fan is moving.  Don't hear any sound, don't feel any air movement, and the metal parts of the case are really hot.

What are we doing wrong?

I should add that when we had Mac OS/X on it, the fan did appear to work properly (a couple weeks ago).  We didn't do the dual boot route so now OS/X is gone.

---

