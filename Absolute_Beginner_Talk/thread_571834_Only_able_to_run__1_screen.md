---
title: "Only able to run  1 screen"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by Smith on 2007-10-09
I seem to find myself in an "interesting" situation. I installed 7.04 AMD 64 yesterday and had some graphical issues in that initially out of the two monitors I have connected only one of them worked. I grabbed the default nVidia drivers and now the other monitor works perfectly (22" widescreen) but the second monitor just is unconfigurable.  I ran gksudo nvidia-settings and switched the terminal on so saw that the reason it was not being accepted was because the EDID for the monitor is non-existent. The refresh rates, supported resolutions etc just aren't there. I'm running 7.04 AMD64 at the moment but it was exactly the opposite way around when I installed Ubuntu 7.04 i386.

I'm more than happy with having my 22" monitor as the primary, I'd just like the other to work as well. Any ideas on how to manually update the EDID file so I can have both? I know the relevant refresh rates and resolutions but just have no idea what to do to have them accepted by the system. The second monitor is a Formac TFT 2010 AU-1 20" monitor but I just cannot get the system to recognise it.

Any suggestions will be gratefully received and I have no fear of command line. It's just that I'm more than a little stumped why this monitor worked perfectly initially but has since just stopped working.

---

### Post by Hospadar on 2007-10-09
If you have a backup xorg.conf file, you could take a look at it and pull the settings out of there.  It would probably be located in /etc/X11 or /var/backups/<somewhere>

---

