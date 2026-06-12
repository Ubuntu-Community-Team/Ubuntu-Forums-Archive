---
title: "Bluetooth problem...Already read the ubuntu BluetoothSetup wiki"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by samad909 on 2007-06-18
Hi, I am facing problems with bluetooth, I can see my dongle when i do a 'hcitool dev'. It is listed with a bluetooth address. When i try to do a 'hcitool scan' i do not see any devices even though my mobile has bluetooth switched on. After some time it shows "Inquiry Failed: Connection Timed Out". I can still find the dongle from the phone, but i cant send stuff to the pc and even cant do a scan from the pc because of the inquiry failed error that comes up..

I am on linux 2.6.20-16 generic with ubuntu 7.04...I am using bluez-utils that already comes with ubuntu...I tried restarting bluetooth and everything....Eventually also tried sudo with the hcitool scan command but still no success.

Any help will be appreciated...

---

### Post by tikey on 2007-08-12
I had the same problem. After I did a 
```
sudo hciconfig hci0 reset
```
I could find the phone with a scan. I still can't connect to the phone but maybe it'll help you.

---

### Post by samad909 on 2007-08-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/121421](https://bugs.launchpad.net/ubuntu/+bug/121421) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Thanks a lot for your reply....I wish the dev guys fix this asap. I also have reported it to ubuntu bugs but have not received a response in a month..

```

https://bugs.launchpad.net/ubuntu/+bug/121421

```

---

