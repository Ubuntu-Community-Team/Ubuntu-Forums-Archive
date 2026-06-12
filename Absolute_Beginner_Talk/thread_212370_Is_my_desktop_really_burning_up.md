---
title: "Is my desktop really burning up?"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by %hMa@?b&lt;C on 2006-07-09
I know there is probably nothing to worry about here, but i was browsing a thread about a laptop and fans not running enough, and my desktop's Aftermarket, too big for the HeatSink, piece of crap fan, runs 100% of the time, doesnt bother me, because the reason that i bought that fan, was because it was the quietest one.  But when I checked the CPU temp, I was shocked.  Is this normal at all, because if this is true, I should be currently engulfed in flames.
```
crowell@ubuntu:~$ acpi -V
     Thermal 1: passive , 4294967040.0 degrees C
crowell@ubuntu:~$

```

---

### Post by Rackerz on 2006-07-09
That's the equivalent of about 42-45 C rite? If so that's normal. Mine's usually about 54.

---

### Post by %hMa@?b&lt;C on 2006-07-09
oh... I was thinking like 42 Billion C.  ok, that makes sense now.

---

### Post by taurus on 2006-07-09
> **jeffc313 said:**
> oh... I was thinking like 42 Billion C.  ok, that makes sense now.

42 Billion C!!!  :shock:

---

### Post by Rackerz on 2006-07-09
> **jeffc313 said:**
> oh... I was thinking like 42 Billion C.  ok, that makes sense now.

Lol. That would be one crispy laptop.

---

### Post by mscman on 2006-07-09
LOL, if it was that hot, there would be no flames, and you probably wouldn't exist anymore... nor would anyone else for that matter! :p I do find it strange that your output gives you that large number, as mine simply says:
```
ahoward@basement:~$ acpi -V
     Thermal 1: ok, 40.0 degrees C
```

Not sure what the issue is there...

---

### Post by b1g4L on 2006-07-09
I believe it's safe to say that your cpu temp isn't anywhere near that temperature. Reboot, go into your BIOS and check readings from there.

---

### Post by wog on 2006-07-09
> **mscman said:**
> LOL, if it was that hot, there would be no flames, and you probably wouldn't exist anymore... nor would anyone else for that matter! :p I do find it strange that your output gives you that large number, as mine simply says:
```
ahoward@basement:~$ acpi -V
     Thermal 1: ok, 40.0 degrees C
```

Not sure what the issue is there...

Unless I miss my guess, the issue is about the placement of the decimal in his returned values and how to fix them so they make more sense. :)

...4294967040.0 degrees C does seem a tad high... :)

---

### Post by digby on 2006-07-10
> **wog said:**
> ...4294967040.0 degrees C does seem a tad high... :)Maybe it's a P4? :rolleyes:

---

### Post by njr on 2006-10-04
I get the same temperature reading:

Thermal 1: passive , 4294967040.0 degrees C

But also get occasional (but increasingly frequent) random reboots with:

Oct  3 14:20:40 chuck kernel: [17179574.136000] ACPI: Thermal Zone [THRM] (-264 C)
Oct  3 16:29:12 chuck kernel: [17179573.656000] ACPI: Thermal Zone [THRM] (-264 C)
Oct  4 00:49:36 chuck kernel: [17179576.836000] ACPI: Thermal Zone [THRM] (-264 C)

---

### Post by bobpur on 2006-10-04
With that laptop and temp I predict a warm winter on the east coast. Please don't fix it 'til spring:)

---

### Post by macogw on 2006-10-04
How do you check the temp from anywhere other than the BIOS?

---

### Post by Pyr3 on 2006-10-04
> **njr said:**
> I get the same temperature reading:

Thermal 1: passive , 4294967040.0 degrees C

But also get occasional (but increasingly frequent) random reboots with:

Oct  3 14:20:40 chuck kernel: [17179574.136000] ACPI: Thermal Zone [THRM] (-264 C)
Oct  3 16:29:12 chuck kernel: [17179573.656000] ACPI: Thermal Zone [THRM] (-264 C)
Oct  4 00:49:36 chuck kernel: [17179576.836000] ACPI: Thermal Zone [THRM] (-264 C)

I'm curious as to the fact it says "passive."  Perhaps there's just a random value stuck in memory or generated for some reason.  Usually it says "ok" or "warning."  Did you set up the sensors packages properly?  I can only tell you to follow the How-To's on the forum, It was kind of hit and miss for me.  

Plus I'm using my laptop (Dell inspiron 8200), since my desktop fell off a truck - literally.  I have the good How-To bookmarked... I'll PM it to you if someone else doesn't first.


Also, should your desktop be running at -264 C, can i buy it to cool my superconducting magnet in my NMR?  I bet it's cheaper then liquid Helium and Nitrogen!

---

### Post by Lord Illidan on 2006-10-04
I think we have a slight problem with overheating here....

---

### Post by njr on 2006-10-05
The temperature reading was from acpi -V. I think passive refers to the fact that I'm using a eMachine T1742 and it doesn't appear to have the capacity for active cooling (that's a guess). I do notice the temperature is 2^32 - 2^8 C. /proc/acpi/thermal_zone/THRM/temperature reports -269 C. This seems to suggest either a bug or a misconfiguration.

Doing cat /proc/acpi/thermal_zone/THRM/trip_points, I see:

critical (S5):           -264 C
passive:                 -273 C: tc1=0 tc2=0 tsp=600 devices=0xe7ceed60
active[0]:               -267 C: devices=0xe7ceee40

I believe I can edit this to change the critical point, but since acpi -V is reading a few milliseconds after the Big Bang, I'm not really sure what to set it to. The freezing point of Hydrogen, maybe?

---

### Post by danramos on 2007-04-07
I got a call from my mom (whom, I might add, I moved off onto Linux back in 2002 and she's quite happy with Ubuntu.. except now...) that her PC was repeatedly rebooting whenever she does certain things.

I tried stressing it out and it seems that if you don't do much it'll keep running--bit if I stress it with too much, it'll run and then eventually turn itself off.  I ssh'ed into it remotely and watched syslog and message files from another computer.

Here's what I got from an idling (non-stressed state):

```
miles@megaframe:~$ acpi -V
     Thermal 1: passive , 4294967040.0 degrees C
miles@megaframe:~$ cat /proc/acpi/thermal_zone/THRM/trip_points
critical (S5):           -264 C
passive:                 -273 C: tc1=0 tc2=0 tsp=600 devices=0xdffef2c0
active[0]:               -267 C: devices=0xdffef798
```

Here's the output I got during the outage...

**SYSLOG**
```

miles@megaframe:~$ tail -n 0 -f /var/log/messages
Apr  7 21:30:50 megaframe -- MARK --

Message from syslogd@megaframe at Sat Apr  7 21:35:26 2007 ...
megaframe kernel: [17183473.516000] Critical temperature reached (-264 C), shutting down.

Broadcast message from root@megaframe
        (unknown) at 21:35 ...

The system is going down for power-off NOW!
Apr  7 21:35:26 megaframe kernel: [17183473.516000] ACPI: Critical trip point

```

**MESSAGES**
```

miles@megaframe:~$ tail -n 0 -f /var/log/syslog
Apr  7 21:30:50 megaframe -- MARK --

Message from syslogd@megaframe at Sat Apr  7 21:35:26 2007 ...
megaframe kernel: [17183473.516000] Critical temperature reached (-264 C), shutting down.

Broadcast message from root@megaframe
        (unknown) at 21:35 ...

The system is going down for power-off NOW!
Apr  7 21:35:26 megaframe kernel: [17183473.516000] ACPI: Critical trip point
Apr  7 21:35:26 megaframe kernel: [17183473.516000] Critical temperature reached (-264 C), shutting down.
Apr  7 21:35:26 megaframe init: tty1 process (3502) killed by signal 15
Apr  7 21:35:26 megaframe init: tty2 process (3503) killed by signal 15
Apr  7 21:35:26 megaframe init: tty3 process (3504) killed by signal 15
Apr  7 21:35:26 megaframe init: tty4 process (3505) killed by signal 15
Apr  7 21:35:26 megaframe init: tty5 process (3506) killed by signal 15
Apr  7 21:35:26 megaframe init: tty6 process (3507) killed by signal 15
Apr  7 21:35:29 megaframe hcid[4108]: :1.3 exited without unregistering the default passkey agent
Apr  7 21:35:31 megaframe kdm: :0[3846]: PAM unable to dispatch function
Apr  7 21:35:31 megaframe kdm: :0[3846]: pam_setcred(DELETE_CRED) for miles failed: Bad item passed to pam_*_item()
Apr  7 21:35:31 megaframe kdm: :0[3846]: PAM unable to dispatch function
Apr  7 21:35:31 megaframe kdm[3816]: Unknown session exit code 0 (sig 11) from manager process
Apr  7 21:35:35 megaframe hcid[4108]: Got disconnected from the system message bus

```

Lastly, the system she uses is: an eMachines T2240 with what appears to be an Intel 845G chipset.  If you want, I can also provide a **dmesg | grep -i ACPI** but held back on posting it here because of length.  It seemed interesting to me but I'm not a kernel coder therefore I wasn't certain that it would be genuinely useful.

Not sure if maybe this should all have been posted elsewhere, but it seems relevant to this thread.  Let me know if you need any further details or directions on where else I should have posted this message.

Thanks!

---

