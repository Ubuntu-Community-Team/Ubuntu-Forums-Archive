---
title: "Xgl login fails"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by CelticWhisper on 2007-02-08
I'm running Kubuntu Edgy on a Pentium 2 400MHz, 640MB RAM, ATI Radeon 9200 w/256MB VRAM.  Frankenstein, I know, but it's generally an okay test system.

I followed the instructions in the "Installing XGL on Kubuntu" guide to the letter with one exception, which was the last step of adding beryl-manager to the startup programs.  I could not find where to do that under KDE's control panel.

I don't know if that's the problem or not, but whatever the case may be, here's the symptom I'm experiencing:

I boot the system and get as far as KDM.  When I select an Xgl session and login, the screen first goes black with only the mouse cursor.  A few seconds after that, I get some horizontal flickery static.  Following that, a few more seconds of blank screen.  At last, I'm dumped back to KDM with no visible explanation of exactly why I couldn't start an Xgl/Beryl session.  I'm able to run a KDE session with no trouble.

What could be causing this?  Is it the beryl-manager application not being added to startup programs that's doing this?

---

### Post by DSn0wMan on 2007-02-09
It is most likely a problem with xgl if you are not starting beryl on startup. It would help if you posted the link to the guide you are following.

If you are using Edgy, there is no need to use XGL, as AIGLX is now built into the xserver.

---

### Post by CelticWhisper on 2007-02-09
Sure.  The link I followed was:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29)

It was from this thread on running Xgl in Kubuntu:
[http://www.ubuntuforums.org/showthread.php?t=354527&highlight=xgl](http://www.ubuntuforums.org/showthread.php?t=354527&highlight=xgl)

Also, I was somehow under the impression AIGLX was only for Nvidia cards, but if it'll work with my Radeon, then great.  Should I try to remove Xgl or just leave it as is and switch over to AIGLX instead?

---

### Post by DSn0wMan on 2007-02-10
Actually AIGLX seems to work better for me with ATI. I have ATI in my laptop, and nVidia in my desktop. The main difference is that AIGLX/nVidia requires using the beta nVidia drive, while AIGLX/ATI works quite well with the OSS ATI driver, and the binary driver.

I would take a look at the beryl wiki. It has been the most reliable source for me.

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

---

