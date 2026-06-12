---
title: "save each boot log"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by krazyman on 2007-03-04
Hi all,

Is there a way to save the last boot log right at startup, so that it's not overwritten by the current boot? I am having an intermittent problem booting (booting seems to stop with a completely black screen) and would like to see what's causing the problem, or at least how far my boot got. All it would need is a "cp boot boot_old" or something, but where would you put it?

TIA,

Andy

---

### Post by x1a4 on 2007-03-05
Hi,

Set the executable bit for _/etc/rc.local_

*sudo chmod +x /etc/rc.local* 

Open _rc.local_ for editing

*sudo gedit /etc/rc.local*

Add this line before **exit 0**

**d=`date +%F-%k-%M` && cp /var/log/boot /var/log/boot-$d**

This will copy the boot log to /var/log/boot-YYY-MM-DD-HH-MM

Where YYYY=Year; MM=Month; DD=Day; HH=Hour; MM=Minute

---

### Post by krazyman on 2007-03-23
Thanks for the reply.

It turns out it was my alsa config that was causing the problem. I fixed it by reinstalling it. I like the way that even tho i messed about and broke it, ubuntu "learned" to mute the sound so that it could still start up! It would fail to boot 2 times, then start up on attempt no 3 with sound muted. I didn't catch on for a bit, because I was leaving the sound muted until a day when I needed it...

Thanks again.

---

