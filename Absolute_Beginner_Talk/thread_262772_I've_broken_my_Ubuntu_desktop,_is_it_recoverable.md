---
title: "I've broken my Ubuntu desktop, is it recoverable?"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by stoer on 2006-09-22
[COLOR="Red"]**[SIZE="5"]Thread ended - problem fixed[/SIZE]**[/COLOR]
Hi,
well after 8 weeks of relative success with Ubuntu and much fun i've finally broken my GNOME desktop.
I was experiencing some annoying problems with sound and decided to follow the following guide [www.ubuntuforums.org/showthread.php?t=205449](www.ubuntuforums.org/showthread.php?t=205449)

and did the following

"Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall Ubuntu. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.
A faster way, is to just remove the problematic packages and reinstall them cleanly.
(1) Remove these packages
Code:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils


(2) Reinstall those same packages
Code:

sudo apt-get install linux-sound-base alsa-base alsa-utils


VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the lsound packages. If this happens, then do the following
Code:

sudo apt-get install gdm ubuntu-desktop


(3) Reboot"

Unfortunately...
sudo apt-get install gdm ubuntu-desktop

only gives me the following

"The following packages have unmet dependencies.
    Ubuntu-desktop: Depends: Gnome-terminal but it is not going to be installed.
E: broken Packages."

I'm then left with just a terminal view and naturally no desktop.

Is this a recoverable situation or am i going to have to reinstall?

Any help (detailed and patient for this "newbie" please) will be very much appreciated.

---

### Post by Stone123 on 2006-09-22
try first:

sudo aptitude update
sudo aptitude install ubuntu-desktop 
sudo dpkg-reconfigure gdm

---

### Post by stoer on 2006-09-22
That fixed it, back up and running.
Guess i'm going to have to be more careful when following guides, especially when somebody warns there might be a problem.
Can't thank you enough for the fix, cheers!

---

