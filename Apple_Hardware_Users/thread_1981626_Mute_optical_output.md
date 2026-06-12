---
title: "Mute optical output"
date: 2012-05-17
forum: Apple Hardware Users
---

### Post by needtosearchforum on 2012-05-17
Hi

I have Ubuntu 12.04 installed on my Macbook Pro 5.5 and on every boot it keeps enabling the optical output. How do i make the mute stick after a reboot?

---

### Post by baloo101 on 2012-05-20
> **needtosearchforum said:**
> Hi

I have Ubuntu 12.04 installed on my Macbook Pro 5.5 and on every boot it keeps enabling the optical output. How do i make the mute stick after a reboot?

Hi, probably same thing here ;)

Open Terminal
type "alsamixer"
Go to "S/PDIF" (not the last one)
Type on your keyboard "M" for mute.

I don't know yet how to save these settings but id'like to ;)
All command are without quotes. I hope this will help you. Have a nice day.

---

### Post by pantropik on 2012-05-20
Use the command:

**amixer set IEC958 off**

To make it permanent either add it to your rc.local or create a script and add it to your startup items.

---

### Post by needtosearchforum on 2012-05-23
> **pantropik said:**
> Use the command:

**amixer set IEC958 off**

To make it permanent either add it to your rc.local or create a script and add it to your startup items.

Thanks. Using this command mutes the optical output but adding it to my /etc/rc.local file doesnt seem to work. I added a redirect to logfile to my rc.local file:


```
amixer set IEC958 off >> /tmp/logfile 2>&1
exit 0
```

And the output of logfile is:
```
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
```

So it seems the amixer command is run during boot but something else enables it when i sign in.

---

