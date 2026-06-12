---
title: "No sound on 20&quot; Aluminum iMac"
date: 2009-03-01
forum: Apple Hardware Users
---

### Post by srojtas@me.com on 2009-03-01
I know this has been answered before.

I have finally installed Linux on my Aluminum iMac (2007).  I am a novice at using the command line, and I was wondering if there are step by step instructions out there (for the beginning Linux user).

2.4 GHz Core 2 Duo

4 GB RAM

Don't care about headphones, just need sound.

Thank you!

---

### Post by roshanjose on 2009-03-01
visit this....this might help you

[http://ossarchives.blogspot.com/2008/10/troubleshooting-your-sound.html](http://ossarchives.blogspot.com/2008/10/troubleshooting-your-sound.html)

---

### Post by cyberdork33 on 2009-03-01
Did you try this:
[https://help.ubuntu.com/community/Intel_iMac#Sound](https://help.ubuntu.com/community/Intel_iMac#Sound)

---

### Post by joecefiro on 2009-03-01
My 2007 20" imac7,1(Aluminium) 2ghz C2D just needed one line added to /etc/modprobe.d/options

1. Open Terminal
2. Type: sudo nano /etc/modprobe.d/options
3. add the following line to the bottom of this file: options snd-hda-intel model=imac24
4. Save the file
5. Reboot
6. Speakers work!

Headphone port dosen't seem to work however, anybody know that part?

---

### Post by cyberdork33 on 2009-03-02
> **joecefiro said:**
> Headphone port dosen't seem to work however, anybody know that part?
If you cannot get it working by messing with alsamixer, then it likely may be a bug. I think this was a problem a long time ago, and now it has come back. Check ALSA's bug reporter:
[https://bugtrack.alsa-project.org](https://bugtrack.alsa-project.org)

---

