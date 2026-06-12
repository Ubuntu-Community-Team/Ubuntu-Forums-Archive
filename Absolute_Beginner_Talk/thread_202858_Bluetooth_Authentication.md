---
title: "Bluetooth Authentication"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by niteblind on 2006-06-24
Hi All,

Back once again I am afraid. I have tried to set up my bluetooth headset to work with skype but i cannot get it to pair with my USB bluetooth adapter. I am using Kubuntu (so gnome fixes arent gonna work i suppose).

The bluetooth adapter seems to be detected by kubuntu fine and installs. When i try to pair the headset though i get "authentication error"

Checking and the USB adapter seems fine:
niteblind@Wolverine:~$ sudo hciconfig hci0 revision
hci0:   Type: USB
        BD Address: 00:09:DD:50:08:D1 ACL MTU: 192:8 SCO MTU: 64:8
        HCI 18.2.1
        Chip version: BlueCore3-ROM
        Max key size: 128 bit
        SCO mapping:  HCI
nitebl

And when I scan the device is found okay but cannot pair. I do not get a prompt to  enter the passcode at all.

trying to manually scan using hcitools scan and the logitech headset gets seen and mac address verified so they are atleast talking if not authenticating.

I have tried look in the Bluetooth section of the KDE system settings and to be honest it does make ANY sense. To confest bluetooth was something i was only a "user" of in windows and so here i am completely lost.

any help would be greatly appreciated.

niteblind

---

### Post by angkor on 2006-06-24
Hi Niteblind,

Try adjusting the security setting in /etc/bluetooth/hcid.conf and make sure your headset is in pairing mode.

```
sudo cp /etc/bluetooth/hcid.conf /etc/bluetooth/hcid.conf_bak
sudo gedit /etc/bluetooth/hcid.conf

```

Go to this section:

        [I]# Security Manager mode
        #   none - Security manager disabled
        #   auto - Use local PIN for incoming connections
        #   user - Always ask user for a PIN
        #
        security **auto**;[/I]

Mine is currently set to auto, but you can try all three to see which one works for you.

After you've changed the setting you need to restart your bluez-utils.

```
sudo /etc/init.d/bluez-utils restart
```

And try pairing your headset again.

Read these pages for more info.

[http://bluetooth-alsa.sourceforge.net/](http://bluetooth-alsa.sourceforge.net/)
[http://www.ubuntuforums.org/showthread.php?t=75978&highlight=kbluetoothd+pin](http://www.ubuntuforums.org/showthread.php?t=75978&highlight=kbluetoothd+pin)

I think you also need to have the sn_bt_sco module to be able to use your headset with skype.

Good luck.

---

### Post by niteblind on 2006-06-24
now i am having a problem with btsco. It isnt instlled on the machine and if i try and search for it the only thing that comes up is bluez-btsco which i apt-get amd then try the command sudo modprobe btsco and it say that is is no present.

Although the headset is being seen by the adapter i am not convinced they are actually pairing as the discovery mode on the headset does not switch off once it is showing in the bluetooth folder.

any ideas?

niteblind

---

### Post by niteblind on 2006-06-24
i take it then that no one can tell me how i get this btsco module installed then?????

niteblind

---

### Post by angkor on 2006-06-26
[QUOTE=niteblind]i take it then that no one can tell me how i get this btsco module installed then?????

niteblind[/QUOTE]

On my system the module is called 'snd_bt_sco'

---

### Post by Copter on 2006-07-20
hi!

in my case it was way easier.

i plugged my Bluetooth USB Dongle. after about 10 secs message poped that Bluetooth device was found. next i just needed to do this (just like **angkor** said)
```


sudo nano /etc/bluetooth/hcid.conf
```
and change in security section
```


# Security Manager mode
# none - Security manager disabled
# auto - Use local PIN for incoming connections
# user - Always ask user for a PIN
#
security auto;
```to
```


# Security Manager mode
# none - Security manager disabled
# auto - Use local PIN for incoming connections
# user - Always ask user for a PIN
#
**security user**;
```
than restart bluez-utils
```


sudo /etc/init.d/bluez-utils restart
```
and viola, it works just the same as when connecting 2 mobile phones. you dont have to edit any other files nor entering MAC adresses.

hope it helps,
copter :]

---

