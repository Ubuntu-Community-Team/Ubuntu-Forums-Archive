---
title: "[SOLVED] scrambled X display after reboot :("
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by KIAaze on 2007-08-16
I messed up my PC somehow by playing with the following command:
```
gnome-screensaver-command --lock
```
in /etc/acpi/lid.sh.

After adding sounds on lid open/close by adding mplayer commands to my lid.sh, the lock session on lid close didn't seem to work anymore.

So I tried adding in the "gnome-screensaver-command --lock" command which worked fine from the command-line to lock the session.

After closing+opening the lid however, I now had an unlocked session, but with a very dark display and I couldn't change the luminosity by using the corresponding laptop buttons.

So I just rebooted, but unfortunately now I have a scrambled X display:
-Globally the image seems to be offset to the left by about 2 cm with the leftmost part reappearing on the right.
-Additionally, it keeps moving some lines so that it looks scrambled.
This problem persists even after several reboots.
What can I do to solve this?

edit:
hardware:
ATI Radeon IGP 345M
Compaq Presario 2500

re-edit:
Note:
I already switched back lid.sh to how it was originally of course and the lock screen works again.
However, it remains scrambled whatever I do. I even tried using an old xorg.conf backup I had and reconfiguring the xserver.

Nothing seems to help. :(

Note:
Maybe I'm wrong and the problem is related to the latest Xorg update for Gutsy:
[http://ubuntuforums.org/showthread.php?t=526947]("http://ubuntuforums.org/showthread.php?t=526947")
How can I revert back to the old version?

---

### Post by kevindubrow on 2007-08-16
Have you tried reconfiguring the xorg file? I messed up mine once and I was told how to fix it here: [http://ubuntuforums.org/showthread.php?t=459208](http://ubuntuforums.org/showthread.php?t=459208) I hope this helps.
-Edit-
Sorry, I skipped over the part where you said that you tried using an old back up. So that link probably won't help. Sorry about that.

---

### Post by KIAaze on 2007-08-23
Problem solved by downgrading **xserver-xorg-video-ati**.
[http://ubuntuforums.org/showpost.php?p=3236714&postcount=19]("http://ubuntuforums.org/showpost.php?p=3236714&postcount=19")

---

