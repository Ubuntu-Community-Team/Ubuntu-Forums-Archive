---
title: "Can PCManFM 1.2 be used to find files on DVD?"
date: 2014-05-26
forum: Apple Hardware Users
---

### Post by Ket_Lubun on 2014-05-26
if not, what should I use to find what's on CD/DVD?

---

### Post by bapoumba on 2014-05-26
Yes it does.

---

### Post by TheFu on 2014-05-26
The **find** command?  It is extremely powerful.   [http://www.tecmint.com/35-practical-examples-of-linux-find-command/](http://www.tecmint.com/35-practical-examples-of-linux-find-command/) has examples.

Obviously, it will only find filenames, but with added options, it can be used to look inside files. If this is a video or audio DVD, then you'll need to look at the content using whatever media player you like.  If DRM was used in mastering the DVD, then the libraries capable of reading passed the DRM are required.  VLC is a good choice, but the DRM libraries will need to be installed separately, if desired, and if legal in your location.

---

### Post by Ket_Lubun on 2014-05-26
Hmm.. mine doesn't.  What could be wrong?  (I do not see "devices".)

---

### Post by bapoumba on 2014-05-26
PCManFM > Prefs > Layout > Tick Devices
PCManFM > Prefs > Volume Management > Tick the first 3 ones (Auto mount on startup and when they are inserted, show options)

---

### Post by Ket_Lubun on 2014-05-26
When Devices is ticked, CD/DVD device shows up.  After top 3 in auto-mount are ticked, nothing shows in the white box under "Don't show available options..." where you have audio CD & Windows software.  I also do not see "untitled DVD" (or any DVD) in the left pane.

---

### Post by bapoumba on 2014-05-26
The "Untitled DVD" is mine, and I did not bother to label it when I created it as a backup for older stuff.
Is what you described hapening after changing the PCManFM prefs _and_ removing/inserting back the DVD ?
What kind if DVD is it ? Can you please try with a data DVD ? Otherwise, you may run into what TheFu described, ie some protected content.

---

### Post by Ket_Lubun on 2014-05-26
Yes, after changing the PCManFM prefs _and_ removing/inserting back the DVD.  It is a data CD that contains a package and firmware downloaded from [here]("https://launchpadlibrarian.net/154410852/b43-fwcutter_018-2_powerpc.deb") and [here]("http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2").

---

### Post by bapoumba on 2014-05-26
Hmm, what is the output to 
```
mount | grep "media"
```

Can you navigate to the CD from PCManFM > FileSystem Root (/) > Media > <your_user> ?

I'll be looking, but I'm not under the impression you would need to logout and log back in for the PCManFM prefs to be taken into account. Would you happen to have a usb stick to insert and see if you see it in the side pane ?

---

### Post by Ket_Lubun on 2014-05-26
mount | grep "media" returns the home directory with not other output

Not sure how to do "PCManFM > FileSystem Root (/) > Media > <your_user>"  BUT "gksudo PCManFM" show no media option.

PS:  I logout, power off my PowerBook G4 then log back in, then inserted the CD.  No difference.

This PowerBook G4 laptop has no USB ports.  WiFi Internet and a CD/DVD drive is all I got.  WiFi is not working without the firmware upgrade that I am trying to do with a CD

---

### Post by bapoumba on 2014-05-27
I have moved your thread to Apple Users where others will help you get your CD/DVD working.

What  I suggested is to navigate from within PCManFM to the /media/<your_user> file where the CD should be mounted. But it obviously does not mount.

Are you using Trusty ? Looking around this issue has been documented for older releases : [https://wiki.ubuntu.com/PowerPCFAQ#CD.2BAC8-DVD_not_mounted.2C_tray_won.27t_stay_open](https://wiki.ubuntu.com/PowerPCFAQ#CD.2BAC8-DVD_not_mounted.2C_tray_won.27t_stay_open)

Now, would it be possible to find an ethernet connection to download the packages from the two links you provided and install them ? How did you install Ubuntu ?

---

### Post by rsavage on 2014-05-28
> **bapoumba said:**
> 
Are you using Trusty ? Looking around this issue has been documented for older releases : [https://wiki.ubuntu.com/PowerPCFAQ#CD.2BAC8-DVD_not_mounted.2C_tray_won.27t_stay_open](https://wiki.ubuntu.com/PowerPCFAQ#CD.2BAC8-DVD_not_mounted.2C_tray_won.27t_stay_open)

That was fixed in 11.10.

---

### Post by Ket_Lubun on 2014-05-28
> **bapoumba said:**
> ...would it be possible to find an ethernet connection to download the packages from the two links you provided and install them ? How did you install Ubuntu ?

The only connection I have is WiFi.  

I installed LUBUNTU 14.04 desktop by burning a CD of the iso file from another computer and used "live video=radeonfb:1024x768-32@60"

---

### Post by TheFu on 2014-05-28
Does the OS show the optical device in **dmesg**? No program can show hardware that is NOT recognized by the OS.
OTOH, I know NOTHING about Apple stuff.

---

### Post by Ket_Lubun on 2014-05-28
Use a workaround with the [alternate PowerPC iso]("http://cdimage.ubuntu.com/lubuntu/releases/trusty/release/lubuntu-14.04-alternate-powerpc.iso") with > install video=radeonfb:1024x768-32@60

PCManFM 1.2 works as expected.  (Now onward with the WiFi issue next)

---

### Post by Ket_Lubun on 2014-05-28
Ha!  alternate install iso also resolved the WiFi driver issue.  Finally!!!

---

### Post by bapoumba on 2014-05-28
Woohoo, glad to see you got it to work :)

---

