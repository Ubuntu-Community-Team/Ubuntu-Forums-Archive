---
title: "Cryptsetup Failed State | Journal Replaying"
date: 2013-01-09
forum: Any Other OS
---

### Post by EnigmaticCoder on 2013-01-09
The past two times I've mounted my external drive, FSCK has told the filesystem to replay journal transactions. Is this a sign that the drive is going bad or can I still get some more use from it? Is there a way to repair the drive? Is there a program that can check for sure if the drive is bad or going bad?
Edit: When I shut down I got 4 beeps (I think) and this is the message in journalctl for each partition:
Failed to deactivate: Invalid argument
[email]systemd-cryptsetup@home.servic[/email]e control process exited, code=exited status=1
Unit [email]systemd-cryptsetup@home.servic[/email]e entered a failed state

Thank you.

---

### Post by EnigmaticCoder on 2013-01-16
Bump.

I'm newly migrated to systemd. I think this is relevant. The journal replays have stopped but crypt devices still fail to deactivate.

---

### Post by EnigmaticCoder on 2013-01-18
Okay, I think I solved it: Had to add the shutdown hook to mkinitcpio.conf and run #mkinitcpio -p linux. I will officially mark this thread as solved after I shutdown the machine several more times and the problem is definitely fixed. Can anyone confirm that this could have been the source of the problem?

---

### Post by EnigmaticCoder on 2013-01-18
That did not work. Problem persists.

---

