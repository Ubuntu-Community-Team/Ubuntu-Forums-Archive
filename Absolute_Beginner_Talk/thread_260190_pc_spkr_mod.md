---
title: "pc spkr mod?"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by Devile on 2006-09-18
ok i do this

sudo rmmod pcspkr

and that turns off the speaker so it doesn't go BEEP when you do something... 

but my problem is, that resets when i turn off my compute,r i have to do it everytime i start my computer... so how do i make it do it permadently????

---

### Post by buffy^ on 2006-09-18
make it a boot script?

---

### Post by nereid on 2006-09-18
Just blacklist the module.

```

sudo -s
echo "blacklist pcspkr" >> /etc/modprobe.d/blacklist
exit

```

---

