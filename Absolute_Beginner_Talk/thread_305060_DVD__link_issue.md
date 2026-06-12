---
title: "DVD / link issue"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by Hurricane on 2006-11-22
Hi all,
Forgive me as I am a newbie with Linux.

I have just installed edgy and am very impressed, but I do have one issue with DVD playback.

If I look in /dev  there is a link in place by default for DVD which links to hdb (obviously doesn't work).

If I delete this link and create a new link along the lines of
**sudo ln -s /media/cdrom0 /dev/dvd**
it works perfectly, until I reboot, and the link goes back to hdb again.

Is there a way of making this link stick between reboots?

Many thanks
Hurri

---

### Post by livestockPimp on 2006-11-22
sure,
write a file and place it in your /etc/init.d folder
type:

#!/bin/sh
(put your link line here or startup code)


after that type at the command prompt

ln -s /etc/init.d/(your filename) /etc/rcS.d/S99(yourfilename)

i think that should work.

---

### Post by livestockPimp on 2006-11-22
what is you do realise that /media/cdrom0 is a mounted device ie; /dev/hda, it would be better to reconfigure the program you watch DVD's in to locate /dev/hdx rather than make a link from mounted media to a device.

---

### Post by Hurricane on 2006-11-22
> **livestockPimp said:**
> 

ln -s /etc/init.d/(your filename) /etc/rcS.d/S99(yourfilename)



Hi there, thanks for the very fast reply.

Just checking if there should be a / between S99 and my filename, or not (as posted)?

Thanks again

---

### Post by Hurricane on 2006-11-22
Hi again,
Ok, I believe I understand what you're saying there.
I was following the insctructions here:
[http://ubuntuforums.org/showthread.php?t=12988](http://ubuntuforums.org/showthread.php?t=12988)

and became unstuck at the point:
"You may also want to make this link permanent (taken from ubuntuguide.org):

$ sudo ln -sf /dev/cdrom /dev/dvd
$ sudo cp /etc/udev/udev.rules /etc/udev/udev.rules_backup
$ sudo gedit /etc/udev/udev.rules
"

as I don't have a udev.rules file

.

I attempted what you suggested but didn't get any results unfortunately, same as before.

I've tried setting my players to hda and hdb but neither seem to work unfortunately.

Do you have any further ideas?

Best regards and thanks
Hurri

---

### Post by livestockPimp on 2006-11-22
i forgot to add to make the script executable
chmod +x (filename)

---

### Post by Hurricane on 2006-11-23
Thanks for all the help, got it to work in the end :)

---

