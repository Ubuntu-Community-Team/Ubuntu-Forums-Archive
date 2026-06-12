---
title: "Odd resolution problem after nvidia-glx-new upgrade"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by teasum on 2008-03-12
Summary: After activating the restricted driver for my nvidia video card, I have an odd resolution switching bug when starting up--it starts up in correct resolution (1920x1200), and then switches to a lower resolution for GDM.  After logging in, it switches back to the correct resolution.  Is this a bug?  What's going on?

Explanation: Everything had been working fine on my laptop (Inspiron 8600), with restricted drivers enabled and no problems.  At some point, for some reason, the 3D capability of my lappy got switched off--I only noticed this when trying to start Armagetron, and nothing happened.  After running it in the terminal, I saw some error that indicated OpenGLX wasn't on or working, and, sure enough, I checked my restricted drivers manager, and it was off.  I have no idea why, but my hunch is that an upgrade somewhere along the way removed support for my particular card.  So, I enabled (re-enabled?) the restricted driver, and it downloaded and installed a couple packages (nvidia-glx-new was the main one, I think).  Then, when I restarted, the resolution was too low. Under Administration > Screens and Graphics, there was no option for the correct resolution of my LCD panel (1920x1200).  However, under Preferences > Screen Resolution, I was able to set the resolution correctly.  

Now, however, I have the problem described at the top of the post: the resolution is off for the GDM screen.  I can tell that the resolution switches because a) it's a laptop and I can see when it's blurry, and b) before GDM opens, the cursor switches locations, indicating a change in resolution.  It should not, as far as I can tell, have to switch resolutions between startup, login, and the desktop.  

This is probably too much detail, but I thought I'd post it in case this indicated a bug of some sort.  Any help would be appreciated.

---

### Post by dcstar on 2008-03-12
> **teasum said:**
> Summary: After activating the restricted driver for my nvidia video card, I have an odd resolution switching bug when starting up--it starts up in correct resolution (1920x1200), and then switches to a lower resolution for GDM.  After logging in, it switches back to the correct resolution.  Is this a bug?  What's going on?

Explanation: Everything had been working fine on my laptop (Inspiron 8600), with restricted drivers enabled and no problems.  At some point, for some reason, the 3D capability of my lappy got switched off--I only noticed this when trying to start Armagetron, and nothing happened.  After running it in the terminal, I saw some error that indicated OpenGLX wasn't on or working, and, sure enough, I checked my restricted drivers manager, and it was off.  I have no idea why, but my hunch is that an upgrade somewhere along the way removed support for my particular card.  So, I enabled (re-enabled?) the restricted driver, and it downloaded and installed a couple packages (nvidia-glx-new was the main one, I think).  Then, when I restarted, the resolution was too low. Under Administration > Screens and Graphics, there was no option for the correct resolution of my LCD panel (1920x1200).  However, under Preferences > Screen Resolution, I was able to set the resolution correctly.  

Now, however, I have the problem described at the top of the post: the resolution is off for the GDM screen.  I can tell that the resolution switches because a) it's a laptop and I can see when it's blurry, and b) before GDM opens, the cursor switches locations, indicating a change in resolution.  It should not, as far as I can tell, have to switch resolutions between startup, login, and the desktop.  

This is probably too much detail, but I thought I'd post it in case this indicated a bug of some sort.  Any help would be appreciated.

Post the contents of your /etc/X11/xorg.conf file, it probably just needs a little "tweaking".......

Actually, on second thoughts do this in a terminal and set the resolution to match your screen:

```
sudo gedit /etc/usplash.conf
sudo update-initramfs -u
```

---

### Post by teasum on 2008-03-13
No luck.  I should mention that the resolution for the usplash screen is fine... just the login screen seems to be set to a lower resolution.  

Any ideas?

[Edit: Here's my xorg.conf file per your original advice.  I hope there's something in here I can tweak.]

---

