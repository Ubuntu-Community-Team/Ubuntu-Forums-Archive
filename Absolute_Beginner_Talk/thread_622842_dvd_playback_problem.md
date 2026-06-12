---
title: "dvd playback problem"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by jinxs1591 on 2007-11-25
I just install gusty on a presario 5000 and got all the needed codecs but for some reason I get this error from all player

totem
Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc.
Please install the necessary plugins and restart Totem to be able to play this media.

Gxine wizard : some please explain what  Im suppose to do here
FAILED - could not access dvdrom: /dev/dvd

Either create a symbolic link /dev/dvd pointing to your cdrom device or set your cdrom device in the preferences dialog.

FAILED - Could not read stats for /dev/dvd.

If you are using the ide-cd module ensure
that you have the following entry in /etc/modules.conf:
options ide-cd dma=1
 Reload ide-cd module.
otherwise run hdparm -d 1 on your dvd-device

No input plugin was found.
Maybe the file does not exist or cannot be accessed, or there is an error in the URL.

when I run totem from the command line I get this
jinx@jinx-desktop:~$ totem
sh: jackd: not found
Gxine from the command line
jinx@jinx-desktop:~$ gxine
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
Fragment program only supported for YV12 data
Please remember I'm a noob that trying to move away from windows

---

### Post by Ub1476 on 2007-11-25
Check out this guide: [How to Play Encrypted (Copyrighted) DVDs in Gutsy]("http://www.ubuntu1501.com/2007/11/how-to-play-encrypted-copyrighted-dvds.html")

---

### Post by jinxs1591 on 2007-11-25
> **Ub1476 said:**
> Check out this guide: [How to Play Encrypted (Copyrighted) DVDs in Gutsy]("http://www.ubuntu1501.com/2007/11/how-to-play-encrypted-copyrighted-dvds.html")


Thank You very much..But still no luck the dvd drive will play vcd but wont read a dvd

---

### Post by marco123 on 2007-11-25
If your on 32bit just run "sudo /usr/share/doc/libdbdread3/install-css.sh" should work after that hopefully.:)

---

### Post by Malta paul on 2007-11-25
Hi, You could use VLC . Down load from Applications>Add/Remove Search for VLC.
The hard way reference is: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) 
Good luck:)

---

### Post by jhenager on 2007-11-25
If you haven't solved this yet, consider Ogle and Ogle-gui. I have used it for a few years, and it works great for me.

---

### Post by jinxs1591 on 2007-11-25
i have downloaded vlc and it still wont work

---

### Post by jinxs1591 on 2007-11-26
> **jhenager said:**
> If you haven't solved this yet, consider Ogle and Ogle-gui. I have used it for a few years, and it works great for me.
tried ogle and still a no go what can I be doing wrong :confused:

---

### Post by Ub1476 on 2007-11-26
> **jinxs1591 said:**
> tried ogle and still a no go what can I be doing wrong :confused:

Did you try to run this in the terminal as Marco said?

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

