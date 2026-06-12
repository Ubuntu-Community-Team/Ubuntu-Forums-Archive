---
title: "Internet Access Problems After Reboot"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by MOkAONE on 2007-03-14
i had internet access earlier today. i needed to change the resolution, so i had to edit some file. blah blah, after rebooting i wasnt able to go online anymore.

i have been referring to "[https://help.ubuntu.com/community/ADSLPPPoE]("https://help.ubuntu.com/community/ADSLPPPoE")" for help

this is wat pops up wen i type "**sudo pppoeconf**" ... a window saying

```
sorry, no working ethernet card could be found. If you do 
have an interface card which was not autodetected so far, you 
probably wish to load the drivers manually using the modconf utility. 
run modconf?

<yes>   <no>
```

after selecting "yes", im prompted with the same window. but wen i close the window, on the terminal, it sais
```
/usr/sbin/pppoeconf: 477: modconf: not found
```

also, under **system>admin>networking**. it used to be a connection called "DHCP", now theres only "Modem Connection".

with "**dpkg -s pppoeconf**"...
```
Package: pppoeconf
Status: install ok installed
```


...hopefully someone can help.

---

### Post by orkim on 2007-03-14
Issue a "sudo ifconfig -a" in a terminal.

What's the output?

-orkim

---

### Post by MOkAONE on 2007-03-14
sudo ifconfig -a
```

lo     Link encap: Local Loopback
       inet addr: 127.0.0.1 Mask 225.0.0.0
       inet6 addr: ::1/128 Scope: Host
       UP LOOPBACK RUNNING MTU:16436 Metri:1
       RX packets:2 error:0 dropped:0 overruns:0 frame:0
       TX packets:2 error:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0
       RX bytes:100 (100.0 b) TX bytes:100 (100.0 b)

sit0  Link encap:IPv6-in-IPv4
       NOARP MTU:1480 Metric:1
       RX packets:0 error:0 dropped:0 overruns:0 frame:0
       TX packets:0 error:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0
       RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

```

---

### Post by orkim on 2007-03-14
There is no eth0 listed.  It doesnt look like you have an ethernet card installed (or at least not as far as Ubuntu is concerned).

Do you know the manufacturer/model of the ethernet card you have?

-orkim

---

### Post by MOkAONE on 2007-03-14
im using the onboard ethernet connection on my mobo (Abit NF8)... i figured that "eth0" was wat i needed to look for, cuz thats wat would come up before i rebooted. 

like i said, i changed the resolution and had to reboot. i was having some problems from before with it taking a long time for it to boot into ubuntu, so i just left my computer running and went out. wen i came back, nothing changed. so i went into my BIOS and changed it back to default mode. it booted up normally, but i wasnt able to go online after that.

---

### Post by orkim on 2007-03-14
You may have disabled the ethernet card (NIC) in the BIOS.  Did you check for this?  The onboard peripherals are usually able to be enabled/disabled in there.

-orkim

---

### Post by MOkAONE on 2007-03-14
ohh wow, i feel like such a n00b. wats exactly wat happened. i fixed that in the BIOS, hopefully it works now.

---

### Post by MOkAONE on 2007-03-14
i tried "sudo ifonfig -a" again, and still getting the same thing.

---

### Post by orkim on 2007-03-14
Hrmmm. You did reboot after this?  It should pick up the hardware change after boot.  I'm wondering if it's not because it's an internal device.  There must be an /etc/init.d/ script for scanning for new hardware.  I'm not certain about that though.

-orkim

---

### Post by MOkAONE on 2007-03-14
i just checked the BIOS, maybe i might have forgotten something else. i guess i was in a hurry to try and see if it would work that i didnt realize that i didnt save the settings, cuz it was still disabled. so if it works, its suppost to auto detect the connection?

---

### Post by orkim on 2007-03-14
If it's enabled, and if you save the settings on exit, and then on the next reboot, Ubuntu should detect that the ethernet card is there.  It will then try to obtain a IP address via DHCP unless you have set it up otherwise.  At that point it should "just work" and you should be back in business.

-orkim

---

### Post by MOkAONE on 2007-03-14
aight, cool... got it running. thanks for all the help orkim :thumbsup:

---

### Post by orkim on 2007-03-14
No problem.  Glad to help.  Good to hear you got it working! :)

-orkim

---

