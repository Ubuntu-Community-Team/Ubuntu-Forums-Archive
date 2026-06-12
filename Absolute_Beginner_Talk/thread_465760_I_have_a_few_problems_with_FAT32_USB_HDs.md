---
title: "I have a few problems with FAT32 USB HDs"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by tabithaboof on 2007-06-06
I have been using Ubuntu for about a month now but I still haven't quite got to grips with the HD/File management. 

I have 3 USB HDs all formated with FAT32 (confirmed with Gparted) all working perfectly under XP. In Ubuntu, a couple of them seem to work just fine. One of them seems to be all wierd and crazy. I named it "archive1"

[IMG]http://i54.photobucket.com/albums/g87/dpurdu/temp/Screenshot.png[/IMG]

I appreciate thats not the most technical of descriptions but under XP it shows up perfectly but under Fiesty there are lots of corrupt files (which are not really there) and a corrupt folder.  I cant delete anything from this HD (corrupt or not) as I get a message saying "read only file system"

I guess my questions are

1 - What are all the garbage files on my HD and how can I get rid of them?
2 - How can I modify the USB HD to have normal read/write/erase permission?

Thanks alot!

---

### Post by viciouslime on 2007-06-06
I would think that actually your drive is corrupt. Linux has probably recognised this and so mounted it as read-only windows however, seems to be quite content with continuing to use it.

I would run some sort of checking tool on it. Scandisk in windows, or ....erm the linux equivalent (I can't remember it's name fsck maybe...)

---

### Post by tabithaboof on 2007-06-07
Thanks I will give that a go

---

### Post by Inxsible on 2007-06-07
Plug that USB stick in Windows and do a "Safely Remove Hardware" on it. Sometimes its just that an unclean removal from Windows locks the drive and you cant have write access to it from Linux.
Or like viciouslime suggested, running fsck on it from the Ubuntu LiveCD might also fix it.

---

### Post by rich.bradshaw on 2007-06-07
Your GNOME looks like it's from 1992!

---

### Post by tabithaboof on 2007-06-07
Thanks for the helpful suggestions, I have tried running scan disk from windows and safely removing but no joy. I am going to try fsck from the live CD next.

> **rich.bradshaw said:**
> Your GNOME looks like it's from 1992!

Hah, you mean my theme? I havent got around to messing with Beryl just yet...

---

### Post by tabithaboof on 2007-06-07
Ok, fsck doesnt seem to work with FAT32 drives as far as I can tell. I am not fanatic about keeping the drive formatted as FAT32 I just want a drive that can be read by Linux and Windows that isnt NTFS. Reason being I have a PS2 which I often hook up to the USB HD to watch movies from  but the PS2 cant read NTFS. 

Are there any other formatting options?

---

