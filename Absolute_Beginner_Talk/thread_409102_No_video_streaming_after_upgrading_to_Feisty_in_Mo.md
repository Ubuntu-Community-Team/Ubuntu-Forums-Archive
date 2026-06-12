---
title: "No video streaming after upgrading to Feisty in Mozilla."
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by keith11 on 2007-04-14
I upgraded to Feisty Beta and for some reason I am not able to play streaming video in Mozilla anymore. I am able to play video in firefox still but not in mozilla browser anymore. I am using Kubuntu. I still have all the files in  "/usr/lib/mozilla/plugins" which are needed to play windows media and real media and stuff but Mozilla web browser is not able to play any online video now. The following is the list of files in my "/usr/lib/mozilla/plugins" folder:

libflashplayer.so      mplayerplug-in-dvx.xpt  mplayerplug-in.so
libjavaplugin.so       mplayerplug-in-qt.so    mplayerplug-in-wmp.so
libnullplugin.so       mplayerplug-in-qt.xpt   mplayerplug-in-wmp.xpt
mozplugger.so          mplayerplug-in-rm.so    mplayerplug-in.xpt
mplayerplug-in-dvx.so  mplayerplug-in-rm.xpt   nppdf.so

Any ideas about what is wrong here? Thanks.

Keith.

---

### Post by keith11 on 2007-04-14
Any suggestions please? Thanks.

Keith.

---

### Post by jviscosi on 2007-04-27
If you open a terminal and start mozilla from there, does it show any error messages when you go to a site that has streaming video?

---

### Post by keith11 on 2007-04-27
I really appreciate your suggestion. I installed Kubuntu 7.04 from scratch and then I installed Automatix2. I installed the prorietory drivers from Automatix2 and everything works fine now.  

Keith.

---

### Post by jviscosi on 2007-04-27
Okay, cool.  I actually stumbled across this thread because the Feisty upgrade completely broke my streaming video in Firefox and Seamonkey and I was wondering if anyone else had had a similar problem.  

In my case, I decided that the problem was the mplayerplug-in because Opera still worked fine, and it was using a custom version of the plugin I had compiled a while back.  I fixed it by compiling the latest version of mplayerplug-in and putting it in place of the one from Feisty, but I didn't want lead off with telling you to do that ... :-)

---

