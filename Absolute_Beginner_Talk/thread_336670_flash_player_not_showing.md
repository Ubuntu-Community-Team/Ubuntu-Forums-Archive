---
title: "flash player not showing"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by monchot on 2007-01-11
i downloaded the latest update of flash from the software update. i tried to go [www.youtube.com](www.youtube.com) ,and no video is showing. what am i doing wrong.

---

### Post by ciscosurfer on 2007-01-11
> **monchot said:**
> i downloaded the latest update of flash from the software update. i tried to go [www.youtube.com]("http://www.youtube.com") ,and no video is showing. what am i doing wrong.Which software update are you referring to?  You can either go [here]("http://labs.adobe.com/technologies/flashplayer9/") and follow the instructions found in the downloaded installer, or do it manually.

---

### Post by monchot on 2007-01-12
synaptic package manager in ubuntu

---

### Post by netadptr0719 on 2007-01-12
I had this problem too, I don't know which one you got but I had to get flash-nonfree for it to actually work with out terrible consequences.

---

### Post by Delkster on 2007-01-12
> **monchot said:**
> i downloaded the latest update of flash from the software update. i tried to go [www.youtube.com](www.youtube.com) ,and no video is showing. what am i doing wrong.

If you enter "about:plugins" in the address bar of your web browser you'll get a list of all plugins that have been installed and are recognised by the browser. Does it list the flash player? Also, did you install flashplugin-nonfree (which is the flash player from Adobe/Macromedia) or some other flash player package in Synaptic? There are others but they're still under heavy development and don't play all flash videos yet.

---

### Post by monchot on 2007-01-20
still not working. am using the 64 bit version of ubuntu.is this the problem

---

### Post by Delkster on 2007-01-27
> **monchot said:**
> still not working. am using the 64 bit version of ubuntu.is this the problem

Unfortunately, yes it is. Adobe hasn't released a 64-bit version of the flash player (not for Linux at least), and you can't combine a 32-bit plugin with a 64-bit browser. You'd have to be running a 32-bit browser as well. There's some [information in the Ubuntu wiki](https://help.ubuntu.com/community/RestrictedFormats/Flash#head-38245bd46a3334b4cc11601e161ddaa63439d2db) if you're determined to get it working but it takes some tweaking. Unfortunately I can't help you further with that since I have no experience of the 64-bit version of Ubuntu.

---

