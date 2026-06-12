---
title: "Alsa driver problem.."
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by rocketboys on 2007-05-17
I installed Alsa, and I could hear the songs but now I can't since I installed pulseaudio driver.
I uninstalled with sypnatic but I still can't here the songs. If I type alsamixer in terminal,
it will come as:

authkey.c: failed to open cookie file '/home/danny/.pulse-cookie': Permission denied
authkey.c: Failed to load authorization key '/home/danny/.pulse-cookie': Permission denied
*** PULSEAUDIO: Unable to connect: Invalid server

alsamixer: function snd_ctl_open failed for default: Connection refused


This. I think I have to reinstall or something. 

Help me Please :'(

---

### Post by k33bz on 2007-05-17
try to unistall then reinstall alsa and see what happens, dont know till you try

---

### Post by Hobo Joe on 2007-05-17
First, completely remove your drivers:

```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```

Then, reinstall:

```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```

Reboot to be safe.

---

### Post by mattva01 on 2007-05-17
<comment deleted>

---

### Post by rocketboys on 2007-05-17
> **k33bz said:**
> try to unistall then reinstall alsa and see what happens, dont know till you try

Thank you for the response!

will do!

---

### Post by rocketboys on 2007-05-17
> **mattva01 said:**
> Hmm you seem to be having lots of permissions issues(from what i've seen of all your questions.). You might want to check if that is the issue.

Thank you for the response!

yeah I'm having lots of weird permission problems..but I don't think this one is because of the permission problem..

---

