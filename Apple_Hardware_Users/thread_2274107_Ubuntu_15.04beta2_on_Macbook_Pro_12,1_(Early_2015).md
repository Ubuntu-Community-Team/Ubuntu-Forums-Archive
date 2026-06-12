---
title: "Ubuntu 15.04beta2 on Macbook Pro 12,1 (Early 2015) - can't turn on Bluetooth"
date: 2015-04-17
forum: Apple Hardware Users
---

### Post by HXn on 2015-04-17
I get no Bluetooth icon in the status bar, and in System Settings > Bluetooth, everything is greyed out (can't turn it on).

[PHP]$ service bluetooth status   
&#9679; bluetooth.service - Bluetooth service   
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)    
Active: inactive (dead)

$ service bluetooth start

$ service bluetooth status   
&#9679; bluetooth.service - Bluetooth service   
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)   
   Active: active (running) since Fri 2015-04-17 18:39:39 CDT; 4s ago
 Main PID: 4070 (bluetoothd)   
   CGroup: /system.slice/bluetooth.service   
           &#9492;&#9472;4070 /usr/sbin/bluetoothd -n

Apr 17 18:39:39 xxxxx bluetoothd[4070]: bluetoothd[4070]: DIS cannot start: GATT is disabled   
Apr 17 18:39:39 xxxxx bluetoothd[4070]: bluetoothd[4070]: Failed to init deviceinfo plugin   
Apr 17 18:39:39 xxxxx bluetoothd[4070]: bluetoothd[4070]: Failed to init proximity plugin   
Apr 17 18:39:39 xxxxx bluetoothd[4070]: bluetoothd[4070]: Failed to init time plugin   
Apr 17 18:39:39 xxxxx bluetoothd[4070]: bluetoothd[4070]: Failed to init alert plugin   
Apr 17 18:39:39 xxxxx bluetoothd[4070]: bluetoothd[4070]: Failed to init thermometer plugin   
Apr 17 18:39:39 xxxxx bluetoothd[4070]: Failed to init gatt_example plugin   
Apr 17 18:39:39 xxxxx bluetoothd[4070]: Bluetooth Management interface initialized   
Apr 17 18:39:39 xxxxx bluetoothd[4070]: bluetoothd[4070]: Failed to init gatt_example plugin   
Apr 17 18:39:39 xxxxx bluetoothd[4070]: bluetoothd[4070]: Bluetooth Management interface initialized   

$ hcitool scan   
Device is not available: No such device[/PHP]

Any ideas? Thanks!

---

### Post by gordintoronto on 2015-04-18
I don't know if this will help or not:

[https://bbs.archlinux.org/viewtopic.php?id=164770](https://bbs.archlinux.org/viewtopic.php?id=164770)

---

