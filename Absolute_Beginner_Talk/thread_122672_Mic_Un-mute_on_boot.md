---
title: "Mic Un-mute on boot?"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by Inkyskin on 2006-01-28
Is it possible to have my microphone automatically un-muted on boot? Its a pain in the butt when I forget to do it after booting and then someone calls on skype ;)

---

### Post by kennethb on 2006-02-14
I'd like to know the answer to this one also. When I use Skype, I always have to un-mute the mic and/or restart Skype.

---

### Post by bountonw on 2006-02-14
I had sound problems that were fixed here.  

[http://www.ubuntuforums.org/showthread.php?t=129246](http://www.ubuntuforums.org/showthread.php?t=129246)

Anyway, I was told to type 

```
alsamixer
```

Then

> Press F5 to view all then press m to mute and unmute everything that looks suspicious!
(If it says there is no such command, then you might need to get a package called something like alsautils from synaptic)


All of my speakers had been muted, after unmuting them, they were unmuted on reboot.  I assume that unmuting the mic would have the same results.

---

