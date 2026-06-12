---
title: "Lubuntu 14.04 Powerbook 5,5 No Sound Failed to register i2c client keywest"
date: 2014-06-30
forum: Apple Hardware Users
---

### Post by Philipp_Rathgeber on 2014-06-30
Hi, 

I've been trying to set up alsa on a Powebook G4 5,5 for days now. 
I tried both snd_powermac and snd_aoa as suggested here:
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

But still not sound :( 

> ~$ cat /proc/asound/cards 
--- no soundcards ---


It seems to me that the sound device is not even recognized: 

> 
$ sudo lspci -vnn
0001:10:17.0 Unassigned class [ff00]: Apple Inc. KeyLargo/Intrepid Mac I/O [106b:003e]
    Flags: bus master, medium devsel, latency 16
    Memory at 80000000 (32-bit, non-prefetchable) [size=512K]
    Kernel driver in use: macio



and here the dmseg 

> [   20.850155] i2c i2c-0: PMac Keywest Audio: attach_adapter method is deprecated
[   20.850165] i2c i2c-0: Please use another way to instantiate your i2c_client
[   20.850171] i2c i2c-1: PMac Keywest Audio: attach_adapter method is deprecated
[   20.850176] i2c i2c-1: Please use another way to instantiate your i2c_client
[   20.850181] i2c i2c-2: PMac Keywest Audio: attach_adapter method is deprecated
[   20.850185] i2c i2c-2: Please use another way to instantiate your i2c_client
[   20.850191] i2c i2c-3: PMac Keywest Audio: attach_adapter method is deprecated
[   20.850195] i2c i2c-3: Please use another way to instantiate your i2c_client
[   20.850200] i2c i2c-4: PMac Keywest Audio: attach_adapter method is deprecated
[   20.850205] i2c i2c-4: Please use another way to instantiate your i2c_client
[   20.850210] i2c i2c-5: PMac Keywest Audio: attach_adapter method is deprecated
[   20.850214] i2c i2c-5: Please use another way to instantiate your i2c_client
[   20.850219] i2c i2c-6: PMac Keywest Audio: attach_adapter method is deprecated
[   20.850224] i2c i2c-6: Please use another way to instantiate your i2c_client
[   20.850237] i2c i2c-6: Failed to register i2c client keywest at 0x35 (-16)
[   20.850243] i2c i2c-7: PMac Keywest Audio: attach_adapter method is deprecated
[   20.850247] i2c i2c-7: Please use another way to instantiate your i2c_client
[   20.850253] i2c i2c-8: PMac Keywest Audio: attach_adapter method is deprecated
[   20.850257] i2c i2c-8: Please use another way to instantiate your i2c_client




anyone an idea how to fix this ?

---

### Post by bapoumba on 2014-07-01
*Thread moved to **Apple Users**.*

---

