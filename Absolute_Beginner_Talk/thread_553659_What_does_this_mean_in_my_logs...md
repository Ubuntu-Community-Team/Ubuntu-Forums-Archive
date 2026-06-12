---
title: "What does this mean in my logs..?"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2007-09-18
Hi,

I keep finding this?

```
Sep 18 15:39:17 lotus NetworkManager: <debug info>^I[1190097557.135039] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_if0_logicaldev_input'). 
Sep 18 15:41:00 lotus NetworkManager: <debug info>^I[1190097660.092506] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_if0_logicaldev_input'). 
Sep 18 15:41:00 lotus NetworkManager: <debug info>^I[1190097660.099847] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_if0'). 
Sep 18 15:41:00 lotus NetworkManager: <debug info>^I[1190097660.114467] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial'). 
Sep 18 15:41:00 lotus NetworkManager: <debug info>^I[1190097660.124364] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_usbraw'). 
Sep 18 15:41:00 lotus NetworkManager: <debug info>^I[1190097660.567123] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial'). 
Sep 18 15:41:00 lotus NetworkManager: <debug info>^I[1190097660.755208] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_if0'). 
Sep 18 15:41:01 lotus NetworkManager: <debug info>^I[1190097661.076684] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_if0_logicaldev_input'). 
Sep 18 15:41:01 lotus NetworkManager: <debug info>^I[1190097661.223876] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_usbraw'). 
Sep 18 15:42:02 lotus NetworkManager: <debug info>^I[1190097722.351481] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_if0_logicaldev_input'). 
Sep 18 15:42:02 lotus NetworkManager: <debug info>^I[1190097722.357150] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_if0'). 
Sep 18 15:42:04 lotus NetworkManager: <debug info>^I[1190097724.211047] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial'). 
Sep 18 15:42:04 lotus NetworkManager: <debug info>^I[1190097724.299234] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial'). 
Sep 18 15:42:04 lotus NetworkManager: <debug info>^I[1190097724.563300] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_usbraw'). 
Sep 18 15:42:04 lotus NetworkManager: <debug info>^I[1190097724.700596] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_if0'). 
Sep 18 15:42:05 lotus NetworkManager: <debug info>^I[1190097725.617681] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_if0'). 
Sep 18 15:42:05 lotus NetworkManager: <debug info>^I[1190097725.632147] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial'). 
Sep 18 15:42:05 lotus NetworkManager: <debug info>^I[1190097725.816445] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial'). 
Sep 18 15:42:06 lotus NetworkManager: <debug info>^I[1190097725.995189] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_if0'). 
Sep 18 15:42:06 lotus NetworkManager: <debug info>^I[1190097726.195852] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_usbraw'). 
Sep 18 15:42:06 lotus NetworkManager: <debug info>^I[1190097726.368166] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_if0_logicaldev_input'). 
```

any ideas?

---

### Post by splintercellguy on 2007-09-18
Looks like good old plug and play to me; are you asking because you have some sort of problem?

---

### Post by hopelessone on 2007-09-18
Doh!!!

thought is was a loose socket USB for the mouse !!!
```
Sep 18 20:53:48 lotus NetworkManager: <debug info>^I[1190116428.815931] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_if0'). 
Sep 18 20:53:48 lotus NetworkManager: <debug info>^I[1190116428.822783] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial'). 
Sep 18 20:53:48 lotus NetworkManager: <debug info>^I[1190116428.850532] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_if0_logicaldev_input'). 
```

is it a broken mouse?

or is this normal?

```
Sep 18 17:13:21 lotus NetworkManager: <debug info>^I[1190103201.134615] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_usbraw'). 
Sep 18 17:13:21 lotus NetworkManager: <debug info>^I[1190103201.431214] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_if0_logicaldev_input'). 
Sep 18 20:53:48 lotus NetworkManager: <debug info>^I[1190116428.815931] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_if0'). 
Sep 18 20:53:48 lotus NetworkManager: <debug info>^I[1190116428.822783] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial'). 
Sep 18 20:53:48 lotus NetworkManager: <debug info>^I[1190116428.850532] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_if0_logicaldev_input'). 
Sep 18 20:53:48 lotus NetworkManager: <debug info>^I[1190116428.915043] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_usbraw'). 
Sep 18 20:53:49 lotus NetworkManager: <debug info>^I[1190116429.705054] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial'). 
Sep 18 20:53:49 lotus NetworkManager: <debug info>^I[1190116429.861637] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_if0'). 
Sep 18 20:53:50 lotus NetworkManager: <debug info>^I[1190116430.278464] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_if0_logicaldev_input'). 
Sep 18 20:53:50 lotus NetworkManager: <debug info>^I[1190116430.315046] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c00c_noserial_usbraw'). 
```

thanks..

---

### Post by hopelessone on 2007-09-18
*bump*

---

### Post by syyid on 2008-07-16
*bump*
Having that show up a bunch of times too - any ideas?
I haven't been adding or removing USB devices in the meanwhile

---

