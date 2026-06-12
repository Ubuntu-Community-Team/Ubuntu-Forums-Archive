---
title: "Bad battery fields on Macbook 13&quot; retina?"
date: 2014-12-03
forum: Apple Hardware Users
---

### Post by chrb on 2014-12-03
Does anyone else have bad battery data?

```
$ egrep -i 'unknown|cycle|model|manu|serial' /sys/class/power_supply/BAT0/uevent
POWER_SUPPLY_STATUS=Unknown
POWER_SUPPLY_TECHNOLOGY=Unknown
POWER_SUPPLY_CYCLE_COUNT=0
POWER_SUPPLY_MODEL_NAME=bq20z4515WGF95571123456789ABCDE
POWER_SUPPLY_MANUFACTURER=SMPNz4515WGF95571123456789ABCDE
POWER_SUPPLY_SERIAL_NUMBER=
 
```

Technology is wrong, model name and manufacturer are too long (first few characters are correct but string is 31 bytes) and serial number is blank. Everything shows correctly under OS X. I presume this is quite rare otherwise it would have been mentioned somewhere.

---

