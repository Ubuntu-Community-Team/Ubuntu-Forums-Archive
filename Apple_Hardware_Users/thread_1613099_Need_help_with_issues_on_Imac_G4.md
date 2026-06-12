---
title: "Need help with issues on Imac G4"
date: 2010-11-04
forum: Apple Hardware Users
---

### Post by tardis2424 on 2010-11-04
Hi there im new to the forums but a log time user of ubuntu. So i recently got given a Imac g4 from work. It does work ( had tiger on it and 'ive run system diagnostics on it).

 So i get it home and get ready to install ubuntu (10.10, power pc of course!). so i try ubuntu 10.10 alternate install and it completes and i end up booting to a red screen and stalls. So i figured ill try 10.04 alterante power pc... Same thing i even tryed the install-powerpc command, same thing...

So out of sheer desperation i tryed 9.04 and it boots and runs fine. The upgrade through check for updates doesnt seem to work either...

I want ubuntu 10.10 as thats what all my other computers are running (about 6 other systems) and im a stickler for all having the same os.

Ive tried searching forums, google. etc and havent found any fixes. So if someone would be kind enough to help me resolve this i would be very thankful!

Open source ftw!

---

### Post by linuxopjemac on 2010-11-04
Which one? Link in everymac.com please.

---

### Post by tardis2424 on 2010-11-04
its this one [http://www.everymac.com/systems/apple/imac/stats/imac_700_fp.html](http://www.everymac.com/systems/apple/imac/stats/imac_700_fp.html) I have upgraded the ram to 1gb if that helps at all, thanks

---

### Post by linuxopjemac on 2010-11-04
You might want to try in a terminal:

```

wget http://mac.linux.be/files/xorg/imac8.txt
sudo mv imac8.txt /etc/X11/xorg.conf
```

reboot.
Tell me if it works. If it does not work, paste me the output of
```
cat /var/log/Xorg.0.log
```

---

### Post by tardis2424 on 2010-11-04
sorry to sound like a total noob here but its running 9.10 are you saying to do that n terminal then attempt the upgrade? Or to try a fresh 10.10 install and somehow do it?

---

### Post by marshag63 on 2010-11-04
tardis2424,
I have the same iMac G4  :)  I somehow managed to get 10.04 installed from a live CD. 

Are you clearing PRAM?  (hold down Command, Option, P and R keys all at once as soon as you turn the power on).  I let it chime at least three times before I try booting off a cd or anything.  

Wishing you good luck - let us know how it goes.

MarshaG.

---

### Post by linuxopjemac on 2010-11-05
With all versions of Linux you will have to set X manually. There is no escape.

---

### Post by tardis2424 on 2010-11-11
I wasnt questioning that i was asking how to do it....

so heres where im at i cleared the pram ,i installed 10.10 alternate off of the cd (had to do alternate cause my unit only has a cd drive and power pcs dont boot off of usb).

it looked ok rebooted and i get the following error - (  16. 964991) fb: conflicting fb hw usage noveaufb vs 0Ffb NVDA,MVMac- removing generic driver and a prompt at which it crashes....

please help a noob fix this i want this system usable!

---

### Post by linuxopjemac on 2010-11-12
use the nv driver instead of nouveau, have a look here:
[http://mac.linux.be/content/xorgconf-files](http://mac.linux.be/content/xorgconf-files)

---

### Post by tardis2424 on 2010-11-12
ok so not to sound ignorant but how do i use said x org file?
So far my konwledge of xorg files is zero....

Honestly ive just basiclly installed ubuntu an used it on my other pc's....

So anyone able to post a tutorial or the commands to do so ( please explain this like you speaking to your grandma, im a linux newb, )

---

### Post by linuxopjemac on 2010-11-12
I told you already in post #4.

Boot into Linux from yaboot with a 1 added, so probably
```
Linux 1
```

then do as in #4.
Then CTRL-D to resume booting

---

### Post by tardis2424 on 2010-11-12
Ok thanks for the clarification much appreciated, sorry for asking so many times....

just learning linux still....

---

### Post by tardis2424 on 2010-11-14
So the Linux 1 command leads to the same error and crash, no terminal cant type a thing....

Any other ideas?

---

### Post by marshag63 on 2010-11-14
Tardis2424,
Try  holding down the "shift" key when you boot Linux 1,etc.  

If that does not work, when you tried 9.04, was it an install or a live cd?  Since you posted that version worked, grab the live cd version of 9.04 and boot it so you have a chance to fix the driver on your installed version.

MarshaG.

---

### Post by simon@syd on 2011-08-31
Got a similar issue. But I dont get a ubuntu login sound, just a red screen of death after the yaboot, boot: prompt - so I dont think Im yet up to the stage where i need to fix xorg stuff. Am going to try ubuntu 9.04, with the alternate install rather than the live one. Or maybe I will download both, no live ubuntu has worked for me as yet, you said 9.04 worked as a live CD/DVD?

---

### Post by rsavage on 2011-08-31
Fixes for screen problems can be found on this thread: [http://ubuntuforums.org/showthread.php?t=1798792](http://ubuntuforums.org/showthread.php?t=1798792)

For example, at the second yaboot prompt type "Linux video=ofonly nosplash"

---

