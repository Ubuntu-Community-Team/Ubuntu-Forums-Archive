---
title: "Dell Inspiron Laptop 1520 sound not working"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by kennyw on 2007-10-21
My laptop is a Dell Inspiron 1520 w/ Audigy soundcard. I am an ABSOLUTE beginner at this stuff and I need help bad. Vista is too consuming to run all the time and I happen to like Ubuntu. Can anyone help?

---

### Post by linux23dragon on 2007-10-21
> **kennyw said:**
> My laptop is a Dell Inspiron 1520 w/ Audigy soundcard. I am an ABSOLUTE beginner at this stuff and I need help bad. Vista is too consuming to run all the time and I happen to like Ubuntu. Can anyone help?

Can you please post the output of this command, from the terminal:-

```

cat /proc/asound/cards
```

And see if you can run the command "alsamixer" in the terminal as well

EDIT:

Please see if you already have sound devices as well:
```

cat  /proc/asound/devices
```

---

