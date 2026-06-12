---
title: "Powermac G4 Problems"
date: 2008-07-02
forum: Apple Hardware Users
---

### Post by Mreyebrows on 2008-07-02
I have an old 350mhz Powerm ac G4 (powerPC processor) with 128 mb of ram and an 80gb hard drive.

i have xubuntu 7.04 installed on it

i have several problems that are just kinda buggin' me.

When i boot the machine, a large Invalid Frequency banner pops up on the monitor. after about a minute, and turning the monitor on and off, it will go straight to the log-in screen.

and the system clock seems to not want to register. It will never have the correct time, and it will force a hard drive check on every boot, with the message:
"43245 days without a HD check. Check forced" but always with some random number for the days.


Any help would be greatly appreciated

cheers

---

### Post by oswaldkelso on 2008-07-02
Battery? does it keep the correct date? My emac needs a new battery and I get funny little messages if I switch it off. I don't as a rule. If I go away it always needs a little "charge" for 10 mins before it will boot :)

---

### Post by Mreyebrows on 2008-07-02
maybe, i doubt it though

---

### Post by stream303 on 2008-07-03
Normally the date bug will prevent gnome from starting up, but based on your error at startup, I'd definitely check it:

```
date
```

[https://help.ubuntu.com/community/UbuntuDateBug](https://help.ubuntu.com/community/UbuntuDateBug)

---

### Post by Mreyebrows on 2008-07-03
gnome will boot and all

it will just force a hard drive boot upon start up


and it will display the correct time when i log in and look at the clock

---

