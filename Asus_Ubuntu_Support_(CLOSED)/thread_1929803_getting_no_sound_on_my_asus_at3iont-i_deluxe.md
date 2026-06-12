---
title: "getting no sound on my asus at3iont-i deluxe"
date: 2012-02-22
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Twiggeh on 2012-02-22
So i've been setting up my new htpc, consisting of the asus at3iont-i deluxe on ubuntu server 11.10.
Everything has been running (relatively) smooth until now.. Im not getting any sound out of my card (i need to get audio from both hdmi and rca outputs), if i type "aplay -l" my machine spits out :

```
aplay: device_list:240: no soundcards found...
```

But if i open alsamixer and press F6 then can see that alsa finds a unit named "HDA NVidia", and i can change the volumelevels etc for it.. But im not getting any audio signal anywhere.

(my alsa is version 1.0.24)

So, now i really dont have any clue of what to do or where to go, im fairly new to *nix (and alsa aswell, for that matter) could anyone point me in the right direction so i can get my sound up?




EDIT : ok, i seem to have found the problem - "linux-alsa-driver-modules" doesnt seem to exist for my kernel (3.0.0-16-server), does this mean i have to downgrade to 10.04 LTS in order to get it working?

---

