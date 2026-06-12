---
title: "VLC player help"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by Extremeshannon on 2008-03-16
Hello all. I have installed VLC and I can get files to play. When I try to open a disk it just won't work. Here is the Device /dev/hdc I have changed to DVD and CDRom still the same any help would be great.

Cheers

---

### Post by thomas7.10 on 2008-03-16
Hi!

In ubuntu the disk devices are on /media..

so just change the device name from /dev/hdc to /media/cdrom0 .

Thomas

---

### Post by Extremeshannon on 2008-03-16
Thanks for the help I change it look there and When i go File > Open Disc Select Dvd and click ok it seems like it might want to work then goes back to the Small VLC player nothing playine

---

### Post by thomas7.10 on 2008-03-16
well it depends how many devices have you got?

it could be cdrom1 as well...

Maybe you should just open the folder /media and look what devices you have and which device is which.

---

### Post by Ub1476 on 2008-03-16
If it's a DVD you bought, it's probably encrypted, which Ubuntu won't play by default (due to licenses..). Look [here]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=(dvd)") to get DVD playback working.

---

### Post by Extremeshannon on 2008-03-16
Thanks for the response everyone. I went thru and installed all software under the restricted directions and set my DVD player's regional code. Still the same thing.

---

### Post by thomas7.10 on 2008-03-16
did you try it with another player, mplayer for example or the standard video player?

---

### Post by Ub1476 on 2008-03-16
Did you do this:

```
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot

```

```
sudo /usr/share/doc/libdvdread3/install-css.sh

```

Or just set the regional code?

---

### Post by Dom[i]no on 2008-03-16
I just had a problem similar to this.  I installed the [libdvdccs]("http://www.videolan.org/developers/libdvdcss.html") package and it solved the problem.

---

