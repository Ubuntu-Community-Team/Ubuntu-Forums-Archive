---
title: "[SOLVED] Restricted Hardware Drivers (To be or not to be)"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-03-01
I just recently managed to install a driver for an NVIDIA GeForce 4 MMX 440 SE. Since doing so, my system tray (sorry for the Windows term please feel free to correct me) There is now an icon of a peice of hardware that says there are restricted drivers available. Does anyone else recommend this? Perhaps I should rephrase for legal technicalities. Would my graphics card truelly run better if I downloaded these restricted drivers? In all actuallity I still don't fully understand these legal technicallities, I was reading about them for a little while when I was figuring out how to get an AVI file to play on my computer yesterday. Is it something like Windows has trademarked certain file extensions? If that's the case, that's total BS. I don't understand though why these drivers are "illegal" when NVIDIA has linux support right on their website! Is it possible that I'm horribly misreading the deffinitions here? Could restricted possibly mean that they were user created and haven't been fully aproved by the upper admins of the Ubuntu Community? Oh so many questions... excuse me for being so inquisitive, I beleive I'll start another thread asking the same questions. Thanks a lot for all your help.

---

### Post by PeterJS on 2008-03-01
They aren't illegal, they just aren't free(libre). Ubuntu sticking with the principle of free software is just telling you that 1) They're not responsible for problems caused by closed code, 2) it's closed code and if you're morally opposed to that giving you a heads up so you can choose not to install them.

If as you say you installed the drivers by hand, there's no point installing the restricted drivers package other than the satisfaction of knowing you installed the drivers the easy/right way the second time.

---

### Post by whoscheesemine on 2008-03-01
So being as they're not free are the drivers pirated if I downloaded/installed them?

---

### Post by PeterJS on 2008-03-01
They are not free as in freedom, you may download and use them, but you may not modify them.

---

### Post by whoscheesemine on 2008-03-01
Oh, okay well thank you for correcting that misconception. So you're saying though, that if I do download these and do not modify them. Then it is completely legal? Also, what would be a good way to find out if these restricted drivers work better than the one I downloaded from the NVIDIA website? Is there a simple method I could take to backup my current driver, try this new one out, and then rollback if I don't like it? Once again you'll have to excuse my windows terminology (when I used ''rollback''). I would love to be corrected though.

---

### Post by PeterJS on 2008-03-01
The drivers you downloaded from Nvida directly and the drivers packaged under the restricted package are the same drivers. In fact all the restricted drivers package does is download them from nvidia, and install and configure them. This is part of the reason that they are none free is because they can not be freely redistributed, it's legal for you to get them from nvidia, it's not legal for ubuntu to give them to you directly. The only thing that's not legal to do with the nvida drivers is give them to other people or modify them.

---

### Post by whoscheesemine on 2008-03-01
So is the restricted drivers notification letting me know of an update for the driver I downloaded off of the Nvidia website? I know sometimes websites will not always have the latest versions of different drivers/software posted on their website, but once you download/install them you can find updates for them. Is this another case of such? Sorry for the millions of questions I just like to make sure I have a full grasp of a concept before I move on.

---

### Post by jocko on 2008-03-01
> **PeterJS said:**
> The drivers you downloaded from Nvida directly and the drivers packaged under the restricted package are the same drivers. In fact all the restricted drivers package does is download them from nvidia, and install and configure them. This is part of the reason that they are none free is because they can not be freely redistributed, it's legal for you to get them from nvidia, it's not legal for ubuntu to give them to you directly. The only thing that's not legal to do with the nvida drivers is give them to other people or modify them.

This is not quite right... The restricted manager does not download directly from nvidias website, it simply downloads a package from the ubuntu repositories and installs it. The ubuntu maintainers **are** allowed to package the drivers into debian packages and re-distribute them.
The drivers you get from the restricted manager are older than the ones you get directly from nvidia, but they are easier to install, and once they are installed you will not need to re-install them after kernel updates, as you will have to do if you use nvidias installer.

Another thing the restricted manager can do is to tell you if you have installed a restricted driver but are not using it.
If you install nvidias driver using their installer, you need to make sure you actually use it.
To do this, you can either manually edit the file /etc/X11/xorg.conf and make sure it says driver "nvidia" (not "nv", "vesa" or anything else), or you can use the restricted manager to do this easier.

---

### Post by PeterJS on 2008-03-01
The notification was letting you know that the driver existed and as far as the package system knows it is not currently installed on your system. The driver is infact installed (and probably much more current than the one restricted drivers would fetch*), but the package system doesn't know about it becaus it was install manually out side the package system so it has no record of the driver being installed.

*This seems to upset some people, but Ubuntu actually locks in a specific version of the driver for testing before making a final release so they can test it to make sure it works and won't break the system, this testing takes time, as a result there's only one stable driver per 6 month release. Some people like the latest and greatest, I'll stick with the one that's been tested and proven not to break my system.

---

### Post by PeterJS on 2008-03-01
> **jocko said:**
> This is not quite right... The restricted manager does not download directly from nvidias website, it simply downloads a package from the ubuntu repositories and installs it. The ubuntu maintainers **are** allowed to package the drivers into debian packages and re-distribute them.
The drivers you get from the restricted manager are older than the ones you get directly from nvidia, but they are easier to install, and once they are installed you will not need to re-install them after kernel updates, as you will have to do if you use nvidias installer.

I knew they were older because of the package freeze, see my last post. But I did not know that Canonical got permission to directly redistribute the drivers. Hmm well you learn something new everyday.

---

### Post by whoscheesemine on 2008-03-01
> **PeterJS said:**
> The notification was letting you know that the driver existed and as far as the package system knows it is not currently installed on your system. The driver is infact installed (and probably much more current than the one restricted drivers would fetch*), but the package system doesn't know about it becaus it was install manually out side the package system so it has no record of the driver being installed.

*This seems to upset some people, but Ubuntu actually locks in a specific version of the driver for testing before making a final release so they can test it to make sure it works and won't break the system, this testing takes time, as a result there's only one stable driver per 6 month release. Some people like the latest and greatest, I'll stick with the one that's been tested and proven not to break my system.

Yeah, I've got to agree with you there, when it comes to going with the one that's tested and proven. Well one of my main focuses with setting this system up is memory allocation. Is the restricted drivers manager up in the System Tray (once excuse Windows lingo) using much memory? How can I get it to go away?

---

### Post by PeterJS on 2008-03-01
> **whoscheesemine said:**
> Yeah, I've got to agree with you there, when it comes to going with the one that's tested and proven. Well one of my main focuses with setting this system up is memory allocation. Is the restricted drivers manager up in the System Tray (once excuse Windows lingo) using much memory? How can I get it to go away?

System tray is as good a name as any, I think technically it's called the "notification area", but I also think everyone knows what you're talking about, and I don't think any one really cares. I believe that specific tray notification is just an offshoot of the update manager that's running all the time anyway so it's memory consumption shouldn't be much beyond the space the icon itself takes up, and the record keeping so the system knows it's there, a couple Kb tops. As for making it go away, I don't know, you could let it have it's way and install the (older) supported drivers over the new one. Maybe, I'm not sure about that, it would probably be fine, but Murphy's law says if I say it's safe it will eat your X config and leave you with no GUI.

---

### Post by whoscheesemine on 2008-03-01
> **PeterJS said:**
> System tray is as good a name as any, I think technically it's called the "notification area", but I also think everyone knows what you're talking about, and I don't think any one really cares. I believe that specific tray notification is just an offshoot of the update manager that's running all the time anyway so it's memory consumption shouldn't be much beyond the space the icon itself takes up, and the record keeping so the system knows it's there, a couple Kb tops. As for making it go away, I don't know, you could let it have it's way and install the (older) supported drivers over the new one. Maybe, I'm not sure about that, it would probably be fine, but Murphy's law says if I say it's safe it will eat your X config and leave you with no GUI.

HaHa :lolflag:Thanks a lot guys. I actually think I'm finally out of questions. Except the one I'm about to post where I'm going to ask if anyone else has the same graphics card and whether or not they they've tried either driver and how they worked for them. So long. (Eh probably not for that long:))

---

