---
title: "Gusty and Network manager."
date: 2008-01-21
forum: Apple Intel Users
---

### Post by joe.gordon on 2008-01-21
I've recently updated to Gusty from Fiesty on my MacBook 2.16 GHz Intel Core 2 Duo. After the update, wireless wasn't working, so I re-installed the Madwifi drivers and wireless worked again. The trouble is now I have two network managers running, and can't figure out how to get rid of just one of them. Any help would be appreciated. Thanks.

Joe.

---

### Post by ronocdh on 2008-01-23
> **joe.gordon said:**
> I've recently updated to Gusty from Fiesty on my MacBook 2.16 GHz Intel Core 2 Duo. After the update, wireless wasn't working, so I re-installed the Madwifi drivers and wireless worked again. The trouble is now I have two network managers running, and can't figure out how to get rid of just one of them. Any help would be appreciated. Thanks.

Joe.
If I read [this]("https://help.ubuntu.com/community/WifiDocs/NetworkManager") right, you can use Add/Remove Programs. Are there multiple entries there? If not, might want to remove what you see, then reinstall MadWifi, but I'm not sure. I'm still using kludgy old ndiswrapper.

---

### Post by bwtranch on 2008-01-23
If it's not causing a problem. I think I would just leave it alone. If you are or experience problems, re-compiling the kernal would probably be what is required (and maybe that is what was needed in the first place). Because this should be running as compiled in the kernal and not as a module, so you may be living on borrowed time anyway.

---

### Post by joe.gordon on 2008-02-04
Thanks for responding guys. I'd almost given up on this. I'm not experiencing any problem yet. What's involved in re-compiling the kernel?

Joe.

---

### Post by cyberdork33 on 2008-02-04
you should not need to recompile the kernel. You can try compiling though if that is what you really want to do. There is a section in the FAQ for compiling a kernel. You can also just port the kernel from hardy though if you want.
[http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)

---

### Post by edm1 on 2008-02-04
you may may just have two networkmanager applets (nm-applet) running. Have a look in your processes list.

---

### Post by joe.gordon on 2008-02-06
I think I've fixed it. I went into the Autostarted Applications menu, under Settings, and found that there was 2 network applets. I removed one, and it seems to have worked. Thanks for all the advice.

Cheers.

---

### Post by cyberdork33 on 2008-02-06
please mark as solved.

---

