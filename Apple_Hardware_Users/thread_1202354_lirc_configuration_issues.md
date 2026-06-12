---
title: "lirc configuration issues"
date: 2009-07-02
forum: Apple Hardware Users
---

### Post by freakalad on 2009-07-02
Running MBR SR 3.1 , Jaunty 9.04 64-bit (fresh installation)

"out-of-the-box", the device seems OK (volume up & down), but having issues with configuration (want to set OOo presentation bindings).

lircd.conf file has required line in:
include "/usr/share/lirc/remotes/apple/lircd.conf.macmini"
which contain the following data:
```

# this config file was automatically generated
# using lirc-0.8.2(macmini) on Tue Dec 11 11:35:26 2007
#
# contributed by Sebastian Schaetzel 
#
# brand:                       Apple
# model no. of remote control: A1156
# devices being controlled by this remote: Mac mini, MacBookPro 15"
# SantaRosa (3.1), MacBook2
#

begin remote

  name  Apple_A1156
  bits            8
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   24
  pre_data       0x87EE81
  gap          211982
  toggle_bit_mask 0x0
  ignore_mask 0x0000ff01

      begin codes
          VOLUP                    0x0B
          VOLDOWN                  0x0D
          BACKWARD                 0x08
          FORWARD                  0x07
          PLAY                     0x04
          MENU                     0x02
      end codes

end remote

```

hardware.conf has the required line in:
START_LIRCD="true"

`cat /proc/bus/input/devices` provides the following relevant info:
```

I: Bus=0003 Vendor=05ac Product=8242 Version=0016
N: Name="Apple Mac mini infrared remote control driver"
P: Phys=/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb7/7-1/7-1:1.0/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=100003
B: KEY=10c0000800 c000000000000 0

```

Trying to set gnome-lirc-properties: 
Manufacturer: Linux Input Device
Model: Apple Mac mini infrared remote control driver

By process of elimination, the device seems to be (& confirmed by cat testing):
/dev/input/event6

IR Remote Control: (tried both ways)
Manufacturer: Apple
Model: A1156

The "Unlock" button never becomes active (even if running app in sudo), nor does it commit/save the changes.
Keeps defaulting to None, None, ADS Tech, USBX-707 

The "update" button downloads the 2,590.5 KiB file, but then crashed with the following error message:
```

Rejected send message, 1 matched rules; type="method_call", sender=":1.73" (uid=1000 pid=10836 comm="/usr/bin/python /usr/bin/gnome-lirc-properties ") interface="org.gnome.LircProperties.Mechanism" member="InstallRemoteDatabase" error name="(unset)" requested_reply=0 destination=":1.76" (uid=0 pid=11191 comm="/usr/bin/python -m gnome_lirc_properties.backend "))

```

`irw` does not return any values.
`ganyremote` confounds me

even tried reinstalling & dpkg-reconfigure 'ing the gnome-lirc-properties

So, strictly-speaking the LIRC IS working, but having a helluva time with the config

Anyone have any advice or help for me, please?

Cheers

- J

---

### Post by clasikowski on 2009-08-13
Hi!

I would advice to remove lirc-gnome-properties, since it does not recognise /dev/input/eventX-devices.

Run a ```
dpkg-reconfigure lirc 
``` afterwards.

so long
hank AKA clasikowski

---

