---
title: "toshiba satellite a135-s4527 intel hda inch7 audio problem"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by newborn on 2008-01-23
i been readin all the forums for gettin my audio issue resolved i dunno how much time i must have cursed ubuntu till now i stopped counting.. i would like to talk to persons who actually ended up resolving their audio issue and how on earth did u guys do it ....
PLEASE HELP :confused:

---

### Post by rickycodie on 2008-01-23
try this, it worked for my wifes satellite.

[http://ubuntuforums.org/showthread.php?t=504096](http://ubuntuforums.org/showthread.php?t=504096)

---

### Post by newborn on 2008-01-23
when i run this command cat /proc/asound/card0/codec#* | grep Codec in the terminal 
i get a message
cat: /proc/asound/card0/codec#*: No such file or directory
m i doing something wrong??

---

### Post by newborn on 2008-01-23
i installed module-assitant and realism and enabled the file and the gid was set appropriately but still my audio icon does not unmute

---

### Post by newborn on 2008-01-23
Loading Realtime Linux Security Module: realtimeFATAL: Module realtime not found.
invoke-rc.d: initscript realtime, action "start" failed.
dpkg: error processing realtime-lsm (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of realtime-lsm-module-2.6.22-14-generic:
 realtime-lsm-module-2.6.22-14-generic depends on realtime-lsm; however:
  Package realtime-lsm is not configured yet.
dpkg: error processing realtime-lsm-module-2.6.22-14-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 realtime-lsm
 realtime-lsm-module-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

Done!
was this the error u said i would see when i finish or is this a real error

---

### Post by newborn on 2008-01-23
# Configuration file for the realtime LSM module
# PARAMETERS can be one or more of:
#
# gid=xx      (allow realtime capabilities for gid xx only)
# any=1|0     (allow any user and process to have realtime)
# mlock=1|0   (allow/disallow mlocking)
# allcaps=1|0 (allow setpcap functionality (dangerous!))

# enable loading of module at startup
ENABLE=yes

# parameter settings for module
PARAMETERS="gid=29"


this is how the realtime - ism file looks like as of now

---

### Post by newborn on 2008-01-26
i finally figured out how to make my headphone only work with out sound emittin from my speakers


FIRST EDIT THE ALSA BASE U MUST HAVE SEEN MANY FORUMS WHICH TELL YOU HOW 
IF U HAD PUT IN THE MODEL VALUE AS "AUTO" OR "3STACK" CHANGE IT TO "LENOVA"


SECONDLY FIND A PATCH FOR REALTEK I DONT HAVE TIME TO UPLOAD THE FILE THANKING UBUNTU FOR ITS SHITTY *** SERVICES
:guitar:
AND JUST RUN THE PATCH IF U DO FIND IT BY JUS CLICKING ON IT FROM THE DESKTOP

IM SORRY I COULDNT BE OF MUCH HELP 

ANYWAYS I WOULD LIKE TO THANK MYSELF FOR HELPING ME
YAY THANK YOU HATS OFF TO YOU

---

