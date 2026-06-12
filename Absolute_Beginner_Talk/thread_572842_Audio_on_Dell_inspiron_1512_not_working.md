---
title: "Audio on Dell inspiron 1512 not working"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by cbut18 on 2007-10-10
Hi,

I'm new to ubuntu but I'm loving it so far. I've gotten it working on my laptop except for the sound doesn't work... 

when i do lspci the device is listed as 

Audio device: ATI Technologies Inc SB600 Azalia

I've searched these forums and googled a fair bit and can't seem to find a fix... 

any help would be great,

thanks

caleb

---

### Post by CAD-MAN on 2007-10-11
Try this:
```
sudo modprobe snd-
``` but press **Tab** instead of enter. If your soundcard is listed, then run the above command with 'snd-yoursoundcard'

Then try running Alsamixer by typing 'sudo alsamixer' in a terminal. Your soundcard may be recognised, but ALSA may have it muted. By running Alsamixer, you should be able to unmute your sound, if that is the problem.

P.S. [https://help.ubuntu.com/community/HowToSetupSoundCards]("https://help.ubuntu.com/community/HowToSetupSoundCards")

P.P.S. I had the same problems on my Inspiron 1520, but managed to figure it out in the end. Look [here ]("http://ubuntuforums.org/showthread.php?t=501195&page=45") (page 38 onwards) for some background reading on 1520 sound issues, and how some of us fixed it.

---

