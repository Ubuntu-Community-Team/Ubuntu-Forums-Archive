---
title: "Man oh man my DVD!!"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by Cysman on 2006-02-07
I'm really sorry, but I'm a fraidy cat when it comes to tweaking anything in Linux.  I'm having a real poor performance with DVD playback and I've tried reading the other threads to find a way to improve it but no success.  I'm using Totem-xine and I think think think I've downloaded all the right codecs and stuff but to no avail.  I'm also having terrible 3D exceleration problems with my ATI Radeon 9800 pro for games even though I followed one of the threads to install the latest driver for it, but I'm not too concerned with that.  I would like to watch movies though.  Am I just stuck not being able to watch DVD in Ubuntu?

Help....

---

### Post by JakeSpeare on 2006-02-07
Well, if you want to do it the easy way, you could install automatix or easyUbuntu. Both of them will look after installing what you need pretty seamlessly. 

Just search the forums for either of those and you should find a howto to install either.

I use automatix on new installs and it works great.

Cheers!

---

### Post by Cysman on 2006-02-07
[QUOTE=JakeSpeare]Well, if you want to do it the easy way, you could install automatix or easyUbuntu. Both of them will look after installing what you need pretty seamlessly. 

Just search the forums for either of those and you should find a howto to install either.

I use automatix on new installs and it works great.

Cheers![/QUOTE]

I did use automatix very early on after I installed Ubuntu and have done it once or twice since then.  That has provided no improvement for my DVD playback.  Do I need to re-install my whole operating system?

---

### Post by JakeSpeare on 2006-02-07
try installing libdvdcss2 from [http://seveas.ubuntulinux.nl/dists/breezy-seveas/all/](http://seveas.ubuntulinux.nl/dists/breezy-seveas/all/) if you cannot play dvd at all.  IF dvd is slow, you should install proper drivers for your videocard.

---

### Post by Cysman on 2006-02-07
libdvdcss2 is already installed, through synaptic I believe, additionally, I believe I have already installed the latest drivers for my ATI 9800 pro.  ???

---

### Post by LordBug on 2006-02-07
If the audio and video are out of sync, I'd suggest making sure DMA mode is turned on for the DVD drive.

---

### Post by JakeSpeare on 2006-02-07
Can you tell us a bit more about the symptoms you are having?  Is it choppy?  NO video?  how many fps are you getting on your 3d acceleration?  

You might try installing vlc.  I find it performs better than totem.

---

### Post by Cysman on 2006-02-07
The video is choppy and at times distorted.  The sound is fine.  I have vlc media player but what I have I'm not familiar with to use it.  The graphical front end isn't user friendly for me.  As far as DMA turned on, how do you check that?  And how do you check the fps?

Oh, wait, here it is:

kenoutten@ubuntubedroom:~$ glxgears -printfps
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
1059 frames in 5.5 seconds = 191.073 FPS
960 frames in 5.2 seconds = 183.981 FPS
960 frames in 5.2 seconds = 185.300 FPS
960 frames in 5.2 seconds = 185.696 FPS
960 frames in 5.3 seconds = 180.121 FPS
1080 frames in 5.6 seconds = 192.831 FPS
1080 frames in 5.5 seconds = 197.471 FPS
1080 frames in 5.5 seconds = 197.438 FPS

Diagnoses?

---

### Post by tseliot on 2006-02-07
[QUOTE=Cysman]The video is choppy and at times distorted.  The sound is fine.  I have vlc media player but what I have I'm not familiar with to use it.  The graphical front end isn't user friendly for me.  As far as DMA turned on, how do you check that?  And how do you check the fps?[/QUOTE]
Try this:
1.  Assuming that /dev/cdrom is the location of CD/DVD-ROM type:  
```
sudo hdparm -d1 /dev/cdrom
```
3.  Then try to watch your film and see if it solved the problem.
4.  To make the settings permanent:
```
sudo cp /etc/hdparm.conf /etc/hdparm.conf_backup 
sudo gedit /etc/hdparm.conf
```
5.  Append the following lines at the end of file
```
/dev/cdrom {
dma = on
}
```
6.  Save the edited file

---

### Post by Cysman on 2006-02-07
[QUOTE=tseliot]Try this:
1.  Assuming that /dev/cdrom is the location of CD/DVD-ROM type:  
```
sudo hdparm -d1 /dev/cdrom
```
3.  Then try to watch your film and see if it solved the problem.
4.  To make the settings permanent:
```
sudo cp /etc/hdparm.conf /etc/hdparm.conf_backup 
sudo gedit /etc/hdparm.conf
```
5.  Append the following lines at the end of file
```
/dev/cdrom {
dma = on
}
```
6.  Save the edited file[/QUOTE]

It tried that and it seemed to help alot as far as the jerky video play, but I noticed that when the DVD player would start to spin up, the same problems would occur.

Ahhg!

---

### Post by tseliot on 2006-02-07
[QUOTE=Cysman]It tried that and it seemed to help alot as far as the jerky video play, but I noticed that when the DVD player would start to spin up, the same problems would occur.

Ahhg![/QUOTE]
You should be able to watch the film with the open source driver "ati" (not fglrx).

Try it

---

### Post by Cysman on 2006-02-08
I went back and did it again and for some reason, it worked!  Thanks alot for the help.

Ken

---

