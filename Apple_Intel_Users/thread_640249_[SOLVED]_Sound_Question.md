---
title: "[SOLVED] Sound Question"
date: 2007-12-14
forum: Apple Intel Users
---

### Post by czechman86 on 2007-12-14
I am looking to add the sound fix that is found in the Macbook wiki, but am confused as to where to add the following lines of code in the '/etc/modprobe.d/alsa-base' section:

```
install snd-hda-intel position_fix=1 /sbin/modprobe --ignore-install snd-hda-intel $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-hda-intel
```

Thanks for your help!

Problem solved

---

