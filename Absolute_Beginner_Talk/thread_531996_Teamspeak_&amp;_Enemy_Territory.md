---
title: "Teamspeak &amp; Enemy Territory"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Dogfighter on 2007-08-22
i know this has been covered a few times, but im still not able to get it working.

those commands should fix it:  
```
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
```

but whenever i enter them i get the error

```
bash: /proc/asound/card0/pcm0p/oss: Permission denied

```

done it with and without sudo, does not make a difference.

btw, i just installed a soundblaster live sound card (did not install anything for it, ubuntu did seem to do everything itself).
onboard sound is deactivated via bios.
ideas? :)
tia

---

### Post by Dogfighter on 2007-08-22
nobody? :(
really wanna get these 2 work together :-k

*EDIT* ive got it sorted.

[http://wiki.ubuntuusers.de/Spiele/Wolfenstein_Enemy_Territory](http://wiki.ubuntuusers.de/Spiele/Wolfenstein_Enemy_Territory)

its in german but the commands can understand everybody :D

---

