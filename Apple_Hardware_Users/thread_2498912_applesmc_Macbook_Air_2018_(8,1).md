---
title: "applesmc Macbook Air 2018 (8,1)"
date: 2024-07-03
forum: Apple Hardware Users
---

### Post by stuartcarrison1979 on 2024-07-03
Hi all

I recently upgraded to noble using a clean install and the t2 image from t2linux.org

Since then I noticed my mbair running hotter than before. I've tried macfanctld and mbpfan. Both are having issues because they try to write fan speed values to fan1_* files in /sys/devices/platform/applesmc.768/, however, my machine no longer has this directory at all. Instead my fan files appear to be in **/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:85/APP0001:00** but these files are not writeable:

[COLOR=#5620F4][FONT=Menlo][COLOR=#39C026]**stuart@SCMBAir**[/COLOR][COLOR=#000000]:[/COLOR]**/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:85/APP0001:00**[COLOR=#000000]$ sudo echo 3000 > fan1_min [/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-bash: fan1_min: Permission denied[/FONT][/COLOR]

After some googling:
I have performed an SMC reset,
modprobe applesmc
removed/reinstalled sensors and run sensors-detect 

The output of sensors *does* show a fan and the fan does spin but only under very heavy loads, I would prefer the fan to start spinning at lower than 75c!)

How can I recreate the previous folder structure and allow mbpfan to be useful, or point mbpfan at these new file locations and make the files writeable?

Thanks for your help

---

### Post by slovenskekasina on 2024-08-06
To address the issue of your MacBook Air running hotter after upgrading and finding that fan control tools like macfanctld and mbpfan are not working due to changes in the system file structure. But first, confirm that the files you found at /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:85/APP0001:00 are indeed the correct ones. You mentioned they are not writable, which is likely due to insufficient permissions.

---

### Post by slovenskekasina on 2024-08-06
Or use custom script, like

#!/usr/bin/env python3


import os


def set_fan_speed(speed):
    try:
        with open("/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:85/APP0001:00/fan1_min", 'w') as f:
            f.write(str(speed))
    except PermissionError:
        print("Permission denied: Unable to set fan speed")


def get_temperature():
    with open("/sys/class/thermal/thermal_zone0/temp") as f:
        return int(f.read()) / 1000


def main():
    temperature = get_temperature()
    if temperature > 75:
        set_fan_speed(6200)
    elif temperature > 55:
        set_fan_speed(4000)
    else:
        set_fan_speed(2000)


if __name__ == "__main__":
    main()

---

