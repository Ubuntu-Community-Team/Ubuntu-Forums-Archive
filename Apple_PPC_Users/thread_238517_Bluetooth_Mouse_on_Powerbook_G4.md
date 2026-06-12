---
title: "Bluetooth Mouse on Powerbook G4"
date: 2006-08-17
forum: Apple PPC Users
---

### Post by ReneB on 2006-08-17
I've got a 1.5 GHz PowerBook G4 with built in Bluetooth. I've been able to install 6.06 and can not make it see my Logitech Mx900 Bluetooth Mouse.

Any advice/suggestons, please?

One last point: This same PowerBook and mouse did have Bluetooth function in Ubuntu 5.

thanks,

Rene

---

### Post by pauljwells on 2006-10-05
you need to swith between hci and hid modes. The default changed going from breezy to dapper

```

sudo hid2hci -1

```

you can add this line to your startup programs in sessions.

If you need to connect to a phone or PDA you need to revert

```

sudo hid2chi

```

hth

---

