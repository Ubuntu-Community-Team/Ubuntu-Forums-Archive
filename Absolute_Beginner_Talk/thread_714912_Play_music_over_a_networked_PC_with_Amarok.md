---
title: "Play music over a networked PC with Amarok?"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by oldsmobile_mike on 2008-03-04
I have a PC running Vista with 1 terabyte of hard drive space, and a laptop running Ubuntu with 80Gb of hard drive space.  Obviously I keep all my movies and audio on the PC, but would like to play them over the network on the laptop.  Movies seem to work fine so far (mostly played with VLC), but I'm having a problem with mp3's.  When I hold the mouse pointer over the icons the music plays, but when I try to open the files in Amarok I get the error "Error Loading Media - No suitable input plugin. This often means that the url's protocol is not supported. Network failures are other possible causes."

What's up with that?

I've found some tips by googling this problem that it can be solved by mapping a network folder, but last time I tried to do that I completely destroyed my network connectivity, and had to spend hours getting it fixed.

Is there an easy solution?

Oh, and to add insult to injury, music files play fine over the network in Rhythmbox, but I like Amarok much more.  :confused:

---

### Post by jordanmthomas on 2008-03-04
It seems like mounting your Vista share as a filesystem in your Linux is the best idea, although you mentioned you messed up last time.

If amarok is unable to play files over smb shares, then you really don't have any other choice unless you want to share the files in a different way.

In general, to mount a smb share you'd just do this (it may need a sudo in front, and /path/to/mount/at must exist):
```
mount -t smbfs -o username=USER,password=PASSWORD //VISTACOMPUTERNAME/SHARE /path/to/mount/at
```

---

### Post by herbster on 2008-03-04
You can also use cifs:

```
mount -t cifs //192.168.1.x/vistabox/share -o username=user,password=pass /mount/point
```

---

### Post by zerhacke on 2008-03-04
This isn't a mounting issue, this is an issue with MP3 Codecs.

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by oldsmobile_mike on 2008-03-04
> **zerhacke said:**
> This isn't a mounting issue, this is an issue with MP3 Codecs.

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)


Are you sure about this?  I remember the codec issue when I first installed Ubuntu, but corrected it the same day I installed the OS.  Currently, Amarok is able to play mp3's just fine if they're stored on the local machine, and Rhythmbox can play them over the network, it's just Amarok that can't play them over the network.  :-(

---

### Post by oldsmobile_mike on 2008-03-04
> **jordanmthomas said:**
> It seems like mounting your Vista share as a filesystem in your Linux is the best idea, although you mentioned you messed up last time.

If amarok is unable to play files over smb shares, then you really don't have any other choice unless you want to share the files in a different way.

In general, to mount a smb share you'd just do this (it may need a sudo in front, and /path/to/mount/at must exist):
```
mount -t smbfs -o username=USER,password=PASSWORD //VISTACOMPUTERNAME/SHARE /path/to/mount/at
```

Thanks!  I tried it first with the cifs option that the other post mentioned, but it gave me a bunch of weird errors about something being blocked, so I re-tried it with the smbfs method.  I was hesitant at first, since when I first tried smbfs it screwed up my whole network connection (I wasn't even able to connect to my router until I removed & reinstalled WICD!), but this time it worked, yay!  :-)

Only question now - how do I make it permanent?  (i.e., not have to run the mount command every time I reboot)...  is there somewhere I can stick this command to have it auto-run?  Perhaps as an entry in sessions?

Thx again!

---

### Post by herbster on 2008-03-04
Could you paste the errors you got on the cifs command?

---

### Post by oldsmobile_mike on 2008-03-04
> **herbster said:**
> Could you paste the errors you got on the cifs command?

I don't have them on my screen any more, but tried googling to find a solution.  These were the search terms I used in google:  "cifs + mount + is not a valid block device"

I found a thread from other people having the same problem:  [http://ubuntuforums.org/showthread.php?t=201406](http://ubuntuforums.org/showthread.php?t=201406)

I also tried that chmod 777 command, but it didn't help, after which I decided to try the smbfs route.

Is there a big difference between smbfs and cifs?  I've heard that cifs is substantially faster than smbfs, can you confirm?

---

