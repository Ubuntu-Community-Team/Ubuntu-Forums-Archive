---
title: "Acer Travelmate 4402 Wi-fi problem Dapper Drake"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by diehardzz on 2006-05-27
Don't know if its the right place to post this. Sorry if I'am wrong.

I follow all the steps to use the broadcom 4318 driver native by ubuntu (without ndiswarpper)

I think the driver is working well, but I cant see my acess point.  See below:

```
diehard@blackbox:~$ iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:"LALA"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.437 GHz  **Access Point: Invalid**
          Bit Rate=11 Mb/s   Tx-Power=19 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

sit0      no wireless extensions.

```

I notice that my radio button led is turned off. When I press it i get:

```

May 27 18:48:42 localhost kernel: [4298894.621000] atkbd.c: Unknown key pressed (translated set 2, code 0xd6 on isa0060/serio0).
May 27 18:48:42 localhost kernel: [4298894.621000] atkbd.c: Use 'setkeycodes e056 <keycode>' to make it known.
May 27 18:48:42 localhost kernel: [4298894.890000] atkbd.c: Unknown key released (translated set 2, code 0xd6 on isa0060/serio0).
May 27 18:48:42 localhost kernel: [4298894.890000] atkbd.c: Use 'setkeycodes e056 <keycode>' to make it known.

```

Searching in google I see that there is a problem with acpi to turn on the button.
The process is a little dificult to me.

Anyone with this laptop know how to turn on the radio button? Help please.

I really want to use my wi-fi.

Thanks ...

---

### Post by harishg on 2006-06-04
Try to post in the wireless network forum.might help

---

### Post by nbcthreat on 2006-06-04
Check this wiki page out for how to set up the broadcom cards.

[https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx)

---

