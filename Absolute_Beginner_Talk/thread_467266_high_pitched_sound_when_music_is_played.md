---
title: "high pitched sound when music is played"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by fred_6666 on 2007-06-07
Hi there! 

When I log on to Ubuntu (version 6.10 Edgy), a very very high pitch sound is given, it also does it when music is played. I have installed codex and plug-ins as required by the error messages, but it hasn't changed anything. 

any ideas?? 

thanks

---

### Post by Hobo Joe on 2007-06-07
First, you should try re-installing the drivers:

```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils

```

Post back the results.

---

### Post by fred_6666 on 2007-06-07
Yh I've done that and now I see no picture and have no sound... all I get is the terminal on boot...

---

### Post by fred_6666 on 2007-06-07
Ok I got the picture back, but I still have the high pitched noise.

Edit: I don't really have the picture back but at least I can login, after that...nothing :S

---

### Post by fred_6666 on 2007-06-07
hi... ok i managed to install ubuntu-deskop... and it worked which is awesome... but no sound at all when wanting to play music on banshee and still have the high pitch sound wen the session logs on..

---

### Post by fred_6666 on 2007-06-09
still nothing on my side... anyone?? please help!

---

