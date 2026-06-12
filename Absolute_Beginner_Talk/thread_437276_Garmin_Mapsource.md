---
title: "Garmin Mapsource?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Insp Gadget on 2007-05-08
I have sort of switched over to Ubuntu but the only program I want to install from Windows is Garmin Mapsource. I understand I need to have Wine installed, which I think it is. Can someone give me step by step directions as to how to install Maosource from just after putting the cd in the drive to having an icon I can click on my desktop?

Thanks!

---

### Post by Martin on 2007-05-10
[http://appdb.winehq.org/appview.php?iAppId=227](http://appdb.winehq.org/appview.php?iAppId=227) Mapsource is not supported under WINE. 
Take a look at vmware or virtualbox if you really need to use that particular software more or less under linux. Also take a look at gpsbabel (in Synaptic) There seems to be a whole lot of stuff for gps devices. Also look at gpsman.

---

### Post by SSamiK on 2007-12-10
I've just gotten Mapsource to run in wine, haven't tested with latest stable but in latest git version it installs and runs fine. Just have to make a symlink from  /dev/ttyUSB0 to  .wine/dosdevices/com1

---

### Post by der_vegi on 2008-01-27
> **SSamiK said:**
> I've just gotten Mapsource to run in wine, haven't tested with latest stable but in latest git version it installs and runs fine. Just have to make a symlink from  /dev/ttyUSB0 to  .wine/dosdevices/com1

You got it to run under wine? Cool! Which version of Wine and Mapsource did you use? Did the uploading of maps work? I really would like to know this, as my father is planning to buy a Garmin GPS and I don't want to buy Windows just for this. Also, it has to be kind of bulletproof, as it is my father. ;)

---

### Post by asmiller-ke6seh on 2008-02-08
> **Martin said:**
> [http://appdb.winehq.org/appview.php?iAppId=227](http://appdb.winehq.org/appview.php?iAppId=227) Also take a look at gpsbabel (in Synaptic) 

GPSBABEL is a data format converter for GPS and Mapping programs.

---

### Post by Daveski on 2008-02-08
[http://ubuntuforums.org/showthread.php?t=439193&highlight=garmin](http://ubuntuforums.org/showthread.php?t=439193&highlight=garmin)

---

### Post by der_vegi on 2008-02-19
With the symlink described above, everything works fine! I am using wine-0.9.46 and MapSource 6.11.6 with Gutsy.

---

