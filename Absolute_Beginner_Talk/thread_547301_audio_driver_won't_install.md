---
title: "audio driver won't install"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by smmalis on 2007-09-09
I just installed Ubuntu (another windows convert) but am having a problem with sound.  I try to install the sound driver, but it never works.  Here is the link to the download: [http://dlsvr03.asus.com/pub/ASUS/mb/socketAM2/M2V/Linux_Audio.zip](http://dlsvr03.asus.com/pub/ASUS/mb/socketAM2/M2V/Linux_Audio.zip)
I know that I have the right motherboard selected.  The driver zip file comes with an automatic installer.  I tried installing it as described in the readme that comes with it, and it does a lot of stuff, but it gives me the following error messages at the end:
/usr/bin/install: cannot create regular file `/usr/sbin/alsactl': Permission denied
make[2]: *** [install-sbinPROGRAMS] Error 1
make[2]: Leaving directory `/home/steven/Desktop/Linux_Audio/alsa-utils-1.0.9a/alsactl'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/steven/Desktop/Linux_Audio/alsa-utils-1.0.9a/alsactl'
make: *** [install-recursive] Error 1
cp: cannot create link `/usr/lib64/libasound.la': Permission denied
cp: cannot create link `/usr/lib64/libasound.so': Permission denied
cp: cannot create link `/usr/lib64/libasound.so.2': Permission denied
cp: cannot create link `/usr/lib64/libasound.so.2.0.0': Permission denied
rm: cannot remove `/dev/sndstat': Permission denied
ln: creating symbolic link `/dev/sndstat' to `/proc/asound/oss/sndstat': File exists
cp: cannot remove `/usr/share/sounds/alsa/test.wav': Permission denied
Remove Folder.....
./install: 89: alsaconf: not found
What should I do?

---

### Post by tgalati4 on 2007-09-09
Try:

>sudo /usr/bin/install

---

### Post by smmalis on 2007-09-10
/usr/bin/install: missing file operand
What now?

---

