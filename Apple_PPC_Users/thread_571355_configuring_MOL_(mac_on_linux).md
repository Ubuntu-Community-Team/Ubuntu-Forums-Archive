---
title: "configuring MOL (mac on linux)"
date: 2007-10-09
forum: Apple PPC Users
---

### Post by frog_pilot on 2007-10-09
I have four problems with configuring MOL.

**1.** When I start MOL, there is only my OS X system volume on the desktop (hda3). How can I manage to mount my data volumes hdb4 and hdb5. They are mounted in Linux. Can I access them directly?

**2.a)** I executed ```
molvconfig
``` it scanned for possible videomodes. Everything worked fine, but I didn't take care of it.  In /etc/mol/molrc.video I substituted the video settings with my actual global video settings 1600x1200@85 but when I change to fullscreen mode, the monitor is flickering as on 60 Hz. Whats wrong? Isn't this video mode supported by MOL video driver ?

**2.b)** I can start fullscreen-MOL with ctrl+alt+F9 but ctrl+alt+F7 don't take me back to the linux-desktop. It seems the shortcuts ctrl+alt+Fx are not working in fullscreen-MOL. Can I change this behaviour?

**3.** For networking I followed these instructions [MacOnLinuxHowTo]("https://help.ubuntu.com/community/MacOnLinuxHowto#head-d2dd4f4483d385601b6f7584ecc9a3567036f980")
> 6) Set up and start MOL using the instructions in the section above. Actually, I had better luck on the networking setup with the sheep driver. I just made the /etc/mol/molrc.net have the line:
netdev:         eth1 -sheep I changed the interface to eth0 due to my configuration, but network isn't working at all. My linux machine has a static IP-address but dhcp-server is also running on my router and could assign a new IP to MOL (If the network with MOL works like this). How can I connect to the network?

Thanks in advance for all your responses :guitar:

---

