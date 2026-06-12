---
title: "Bluetooth (Pairing problems!) Please Please Help"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-06-16
I do not know much about bluetooth but I have been off and on been trying to get this to work for about 2 years now.

At the moment I'm using feisty and thought that maybe I will have another go, everything else seemed to get better maybe bluetooth did also.

So I installed bluez-utils
```

sudo aptitude install bluez-utils

```

This is what happens

hcitool dev
```

Devices:
        hci0    00:XX:XX:XX:XX:C3

```

hcitool scan
```

Scanning ...
        00:XX:XX:XX:XX:47       V360v
        00:XX:XX:XX:XX:45       Nokia 6275i

```

sudo hcitool cc 00:XX:XX:XX:XX:45
sudo hcitool auth 00:XX:XX:XX:XX:45
```

Not connected.

```


I have no idea where to go from here!!!

---

### Post by PartisanEntity on 2007-06-16
Perhaps you have tried this already, but have you considered initiating the pairing from the Nokia for example? I found that to be the easiest way.

The package you would need, if you are using Gnome is: buez-gnome and bluez-pin as well as gnome-bluetooth if my memory serves me correctly.

---

### Post by guysmiley25 on 2007-06-16
Ok so I installed bluez-gnome, bluez-pin and gnome-bluethooth.

bluez-gnome was already installed as a dependency of bluez-utils.

I tried pairing from my mobile, however still was asked for a passkey. again tried 1234, 1111, 0000. None of theses worked.

I tried paring using hcitool.
```

sudo hcitool cc 00:XX:XX:XX:XX:45
sudo hcitool auth 00:XX:XX:XX:XX:45
Not connected.

```

Still no change.

However gnome-bluetooth added a program to my menu called "Bluetooth File Sharing" If I send a file to the computer from the phone, this program picks it up and downloads it. This is pretty cool, but I still want my phone to pair with the computer.

Please Please Please!

Thanks PartisanEntity

---

### Post by guysmiley25 on 2007-06-22
Come on guys!

Also I would add that I'm using Xubuntu Feisty Fawn.

Thanks

---

### Post by borahshadow on 2007-06-22
I think you set the passkey in /etc/bluetooth/hcid.conf
Hope that helps

---

### Post by arcx.rw on 2008-05-20
Check this [http://grumpymole.blogspot.com/2006/11/xubuntu-bluetooth-callpasskeyagent-no.html]("http://grumpymole.blogspot.com/2006/11/xubuntu-bluetooth-callpasskeyagent-no.html")

---

