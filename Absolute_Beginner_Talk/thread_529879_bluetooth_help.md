---
title: "bluetooth help"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by finer recliner on 2007-08-19
i purchased a belkin bluetooth adapter today to connect my samsung u740 cell phone to linux. but hcitool scan doesnt find anything :(


i've been following the directions here: [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

my adapter is recognized:
```

$hcitool dev
Devices:
        hci0    00:0A:3A:7B:D9:93

```

and i get the bluetooth manager icon in the upper right corner of the screen (and says it placed my device in discovery mode)

so i put my phone into discovery mode and run:
```

$ sudo hidd --search
Searching ...
$ sudo hcitool scan
Scanning ...
Inquiry failed: Connection timed out

```


my phone is sitting right next to the computer when i do this (so its not out of range). any ideas?:confused: 
thank you in advance

p.s. im running feisty fawn (7.04)

---

### Post by finer recliner on 2007-08-20
update: i installed the drivers on my windows partition. and it works fine. i can communicate w/ my phone via bluetooth just fine in windows. linux...not so much :(

---

