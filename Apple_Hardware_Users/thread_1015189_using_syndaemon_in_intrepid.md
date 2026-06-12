---
title: "using syndaemon in intrepid?"
date: 2008-12-18
forum: Apple Hardware Users
---

### Post by chris.h on 2008-12-18
I can't get syndaemon to run in intrepid for me. I'm thinking it's because I'm using fdi instead of xorg.conf? 

When I run syndaemon -t -d i get:
```

X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  146 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```

Right now I have a /etc/hal/fdi/policy/tpad.fdi file that's got:
```

 <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="appletouch">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.SHMConfig type="string">on</merge>
```

Now the only difference I see between the xorg files and the fdi is the reference to the input device being "Synaptics Touchpad." Is there an option to enter this in my fdi or do I need to add variables to the xorf.conf file?

right now my xorg.conf file makes no reference to the touchpad or synaptics.

---

### Post by cyberdork33 on 2008-12-19
well, SHMConfig does have to be enabled, that that message is indicative that it is not. I see that it is in your fdi configuration, but it may not work. What are you trying to do with syndaemon? Maybe there is another way to do it.

---

### Post by chris.h on 2008-12-19
I'm trying to have taps be ignored while typing.

---

### Post by cyberdork33 on 2008-12-19
> **chris.h said:**
> I'm trying to have taps be ignored while typing.

you could attempt to tweak mouseemu to do this... or you could try adding the SHMConfig option to your xorg.conf, but doing that might break the fdi configuration.

---

### Post by chris.h on 2008-12-19
> **cyberdork33 said:**
> you could attempt to tweak mouseemu to do this...

lol i think i removed mouseemu to make my caps lock light work...

---

