---
title: "Connecting to Nokia Phone, need some help and recommendations"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-01-31
I have a new [Nokia 6275i]("http://www.nokia.co.nz/nokia/0,8764,93252,00.html") and I would like some help connecting it to my computer.

If possible I would like to be able to use the phone as a Dial up modem?

How should I connected the phone to the computer? Data Cable, Blue tooth, IR. I have a cable called DKU-2 for my old phone from my Windows days, but I do not thing it will work.

I would like to be able to synchronize my contacts with Thunderbird, and amsn, I'll be happy with exporting them to a CSV. 

What software is there and what should I use?

Any help would be awesome!

---

### Post by livinginx on 2007-01-31
Well, I have an N90, usb functioning doesn't work (currently).

You could probably bluetooth with it, I haven't any experience.  But I know that the same generation of Nokia's that use the same Symbian OS version as the N90 have VERY limited support.

---

### Post by guysmiley25 on 2007-02-01
OK just some questions.

What is N90, is that the generation? If so is that what generation my phone is?

Also was still wondering about the software. Whether or not that I use Data Cable, Bluetooth, or IR. It will still be the same software right? So what software should I be looking at?

Thanks for the help livinginx.

---

### Post by guysmiley25 on 2007-02-02
Bump!

---

### Post by guysmiley25 on 2007-02-02
Ok so I went out a bought a Bluetooth USB Doggle and all is well.

But when I run:

```
gnokii --identify
```

I get this output:

```

GNOKII Version 0.6.13
LOG: debug mask is 0x1
phone instance config:
model: 6510
port_device: XX:XX:XX:XX:XX:XX
connection_type: 5
init_length: 0
serial_baudrate: 19200
serial_write_usleep: -1
hardware_handshake: 0
require_dcd: 0
smsc_timeout: 100
connect_script: 
disconnect_script: 
rfcomm_cn: 1
sm_retry: off
Connecting
Serial device: opening device XX:XX:XX:XX:XX:XX

```

Then on my phone I put in the default 1234 pin and get:

```

Can't connect: Connection refused
Couldn't open PHONET device: Connection refused
Error in link initialisation: 1
Telephone interface init failed: Command failed.
Quitting.
Serial device: closing device

```

By the way for the model part I put model: 6510 but that was just a guess as I do not know what to put.

---

### Post by mimsmall on 2007-03-26
Gnokii connects to lots of phones for synchronization. xgnokii is available using synaptic. gnapplet is required to communicate with phones that use Symbian os. All this stuff is on the Gnokii web site.

---

