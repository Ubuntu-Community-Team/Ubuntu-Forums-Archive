---
title: "iMac G4 no sound"
date: 2008-07-13
forum: Apple Hardware Users
---

### Post by fraterf93 on 2008-07-13
Hey Guys!  I have installed Xubuntu Hardy on my iMac G4 1 Ghz, 256 MB, and I have no sound.  The xfce-mixer shows no device.  Also there is no sound if I load Ubuntu either.  Of course, I do have sound in Tiger.  I don't think it's a hardware issue.  I've searched the forums, and didn't find any similar issues from other users.  Help!

    On the other hand, I've been using Ubuntu PPC and it's variants since the Badger days, and this is by far the best release.  DVD playback with VLC (Totem is worthless, and should be smote from the earth), I'm also *very* impressed with the fact that my Airport wireless was so easy to get working, and has worked so flawlessly.  Now if only I could play my DVDs with sound!

---

### Post by stream303 on 2008-07-14
Try running alsamixer in a terminal, and seeing if your speakers are muted. (m-key to toggle mute).

Alsamixer worked for me, even when the gui counterparts wouldn't - even though they would *indicate* mute on/off, they weren't actually doing it. :)  Alsamixer to the rescue. :)

Also possible PulseAudio issues - you may want to fall back to Alsa audio as a quick test in the sound prefs...

---

### Post by fraterf93 on 2008-07-16
OK its not seeing my sound hardware 

[IMG]http://farm4.static.flickr.com/3196/2673543655_da20de478c.jpg?v=0[/IMG]


[IMG]http://farm4.static.flickr.com/3134/2674366626_a684c9a556.jpg?v=0[/IMG]

---

### Post by stream303 on 2008-07-17
I think your machine uses the powermac audio.  Check out this thread even though it talks about the ibook:

[http://ubuntuforums.org/showthread.php?t=785360](http://ubuntuforums.org/showthread.php?t=785360)

Maybe doing a sudo modprobe snd-powermac will revive it!  In addition to this you may have to load the smp kernel as per the bug reports.

---

### Post by fraterf93 on 2008-07-26
Thx!  The sudo modprobe snd-powermac worked perfectly! I was able to find and configure my sound hardware, and get the voulume going!\\:D/

---

### Post by motsteve on 2008-07-26
I'm not an expert here, but I think to get your sound to always work, you'll have to add the power mac sound module to the list of modules that are accessed during boot up.  All I remember when I did it was that the file was somewhere in the /init.d subdirectory.  Take a look around on this.  I'm glad your sound is working, it's a bummer when it's not. :-)

Steve

---

### Post by johnrobert on 2008-07-26
Thanks motsteve. I just installed Hardy on my G4 powerbook and also had no sound until I used modprobe as you suggested. Still have to find out how to make the fix permanent but it is nice to listen to my CDs while I'm at it.

---

### Post by stream303 on 2008-07-26
You can just add it to the end of /etc/modules

```
sudo nano -w /etc/modules
```
CTRL-O to write out your changes, CTRL-X to quit the editor.

[https://wiki.ubuntu.com/PowerPCFAQ#head-80b3759a67892a1cd602386a1cad3bae8cb1835e](https://wiki.ubuntu.com/PowerPCFAQ#head-80b3759a67892a1cd602386a1cad3bae8cb1835e)

Glad to hear (pun intended) it up and running! :)

---

