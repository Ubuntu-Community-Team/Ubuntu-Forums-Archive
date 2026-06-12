---
title: "Loaded Kubuntu"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by Vinillum on 2008-04-06
When entering Kubuntu environment, 1 out of 20 times I get the wrong resolution. Mine is set to 1280*1024, but those rare times I get like 1600*1200. Logging out and logging in again seems to work. Any ideas why is this happening?

P.S. Is that normal that login screen is also larger than my settings? I don't have problem with that, but still, is that normal?

---

### Post by leonidas666 on 2008-04-06
> **Vinillum said:**
> P.S. Is that normal that login screen is also larger than my settings? I don't have problem with that, but still, is that normal?
As far as i know, the Login Screen uses the resolution set in the xorg.conf file. Once proper KDE takes over, you can change the resolution through the kde settings - however, that is a per-user setting, so this won't change the setting for the login screen.
If you run your computer with only one resolution anyway (in your case 1280*1024), you could try changing your xorg.conf, so that the resolution does not have to change when you actually login.

---

### Post by indytim on 2008-04-06
I've had the same problem since day 1 of Gutsy.  Truth be told, I'm too busy with other things in the ops to dink around for a permanent fix.  My "resolution" on the resolution problem when it occurs is to simply <ctrl><backspace> and re-log in.  Works 100% of the time. 

Haven't started testing the next release so don't know if it's a fix yet.

IndyTim

---

### Post by indytim on 2008-04-06
Sorry about that... it should be 

<ctrl><alt><backspace>

:)

IndyTim

---

### Post by Vinillum on 2008-04-07
Thanks Leonidas, it worked very well... My login screen is now in 1280*1024 resolution... Tanks a lot

---

