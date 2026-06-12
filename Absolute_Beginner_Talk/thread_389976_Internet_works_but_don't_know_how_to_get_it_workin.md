---
title: "Internet works but: don't know how to get it working straight from boot"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by brunoba on 2007-03-21
Hey ppl, this is my first post.
Before anything else, i must disagree with some saying the forum is of no help. It was mainly by reading the forums that i could get Edgy up and working. Long live the forums........

Ok the problem i'm having is:

I could manage to set and config wpa_supplicant, wireless driver, interfaces and all that. Now i'm able to access the internet after 3 simple steps taken after boot.

1st - kill the wpa_supplicant process that's already running from boot
2nd - open terminal, then:

sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf -wB -D wext

3rd - Then i run dhclient and it works.

Dhclient won't connect unless i kill the old wpa process and start a new one with those parameters.
But since other users of this computer know even less linux than me....i wanted it to connect straight from boot, no manual killing and running needed. I don't know where and how to do that, and would really appreciate any help on the matter.

Thanks in advance....
bruno

---

### Post by bdogg64 on 2007-03-21
You could install the network-manager-gnome which handles everything for you. It works pretty well.

sudo apt-get install network-manager-gnome

or

sudo apt-get install network-manager-kde

---

### Post by brunoba on 2007-03-21
tried it already, at my first failed attempt to get internet working.....

i'll try again....
but my question is:
why does a wpa_supplicant runs from boot, where is it ran from, which parameters are set there that won't work unless i kill this and start a new one

---

### Post by dracomordag on 2007-03-21
i agree that the above would be easiest.

however, you can go into your boot processes (system->preferences->sessions: startup programs, add) and add those three commands you just listed to what's run at boot!

---

### Post by lamalex on 2007-03-21
or write a little bash script.
```

#!/bin/sh
your commands that fix it for you

```
chmod to make it executable,
then add that script to startup sessions and you are good to go

---

