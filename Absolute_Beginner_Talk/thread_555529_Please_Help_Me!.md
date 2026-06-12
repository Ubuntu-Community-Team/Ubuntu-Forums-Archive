---
title: "Please Help Me!"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by l1nuxxx on 2007-09-20
Hi there everyone. I have just installed Linux for the first time on my pc. Its an older laptop(compaq armada 1750 to be precise). All is good except i cant get the sound card to work. I have tried various commands from the terminal but it just says that there is no device. I have had a llok around he forum and it seems to be a common occurance and i was wondering what the solution was. I have the Linux bible so i have loads of other distros to try. Any suggestions!

---

### Post by kvonb on 2007-09-20
You should find the answer to your problem here:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Jeroen Vernooij on 2007-09-20
Please go to
system-> preferences -> sound
and at 'sound playback', choose the various options, and press test. Maybe OSS for example does work.

---

### Post by mali2297 on 2007-09-20
If the link in kvonb's post doesn't help you, run the commands below in a terminal and post the output.
```

aplay -l
lspci | grep -i audio
cat /proc/asound/card0/codec#* | grep Codec
uname -a

```

---

