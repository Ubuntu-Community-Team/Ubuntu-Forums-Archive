---
title: "Startup problem"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by dangerpl on 2007-04-21
Hi, is there a way to run a command in the terminal after each reboot automatically? Unfortunately, I have a sound issue that can't be resolved otherwise :( I have to run the following command after each reboot:
```

 kill $(lsof -t /dev/dsp* /dev/audio* /dev/mixer* /dev/snd/*) ; sudo modprobe -r $(lsmod |grep ^snd |awk '{print $1}') && sudo modprobe snd-hda-codec && sudo modprobe snd-hda-intel model=auto
```

If anyone knows how to do it, please help? Thanks :)

---

### Post by mrvertigo on 2007-04-26
you could set a shell script to do it upon boot time by entering it into your boot config, or place it into a shell script and simply execute it rather than typing it every boot.

---

