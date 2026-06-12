---
title: "Old laptop ACPI problem"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by Sanych on 2006-05-10
Hello!

I am using 5 years old laptop, RoverBook Voyager B410L (model code
D220S). Ubuntu 5.10 was successfully installed on it and all work fine
except:

- modem
- batter and AC adapter monitors

I was googling a lot and spent a lot of time trying to find solution in
discussion boards but still had no luck.
Here are few outs from commands I found on forums (in the moment
commands execution battery was fully charged and ac adapter was plugged
in):

[I]acpi -V
     Thermal 1: ok, 52.0 degrees C
  AC Adapter 1: off-line

cat /proc/acpi/battery/state
cat: /proc/acpi/battery/state: No such file or directory

cat /proc/acpi/ac_adapter/ADP0/state
state:                   off-line

dmesg | grep acpi
[4294744.410000] ibm_acpi: hkey object not found

dmesg | grep ACPI
[4294743.963000] ACPI: AC Adapter [ADP0] (off-line)
[4294744.129000] ACPI: Power Button (CM) [PWRB]
[4294744.129000] ACPI: Sleep Button (CM) [SLPB]
[4294744.129000] ACPI: Lid Switch [LID]
[4294756.815000] apm: overridden by ACPI.

[/I]Here are custom errors from dmesg:

[I][4294669.749000] ACPI: Embedded Controller [EC] (gpe 23)
[4294669.849000] read EC, IB not empty
[4294669.849000]     ACPI-0423: *** Error: Handler for [EmbeddedControl]
returned AE_TIME
[4294669.849000]     ACPI-0508: *** Error: Method execution failed
[\_SB_.BAT0._STA] (Node cded77a0), AE_TIME
[4294669.849000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294669.849000] pnp: PnP ACPI init
[4294669.905000] Error in acpi_ec_wait
[4294669.955000] read EC, IB not empty
[4294669.955000]     ACPI-0423: *** Error: Handler for [EmbeddedControl]
returned AE_TIME
[4294669.955000]     ACPI-0508: *** Error: Method execution failed
[\_SB_.BAT0._STA] (Node cded77a0), AE_TIME
[4294669.955000]     ACPI-0171: *** Error: Method execution failed
[\_SB_.BAT0._STA] (Node cded77a0), AE_TIME[/I]

From the very beginnig I tried to find &#1074;&#1099;&#1074;&#1077; specific for my machine on acpi.sf.net - but there is no such for model :(

Any advices, additional links or howto would be great!
Thanks!

---

