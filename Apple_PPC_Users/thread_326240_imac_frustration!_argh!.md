---
title: "imac frustration! argh!"
date: 2006-12-27
forum: Apple PPC Users
---

### Post by paul7458 on 2006-12-27
I have 6.0.6 live cd. I fixed the video. I have an arrow on a brown screen then several hours later all I have is a purple screen with no arrow. And yes the hard drive is still spining. Oh it's a grape imac dv. Other than the xorg settings is there anything I missed? I also set the default color depth to 8 to use less memory. Is there anyway to do a text based install without the alternate cd? Can I make this work or is the live cd on this 'puter a lost cause?

---

### Post by tagra123 on 2006-12-27
> **paul7458 said:**
> I have 6.0.6 live cd. I fixed the video. I have an arrow on a brown screen then several hours later all I have is a purple screen with no arrow. And yes the hard drive is still spining. Oh it's a grape imac dv. Other than the xorg settings is there anything I missed? I also set the default color depth to 8 to use less memory. Is there anyway to do a text based install without the alternate cd? Can I make this work or is the live cd on this 'puter a lost cause?

  Does the ppc regular install disk have an expert mode?

I used the alternate cd in expert mode -- actually I installed up to the base system and then skipped to install yaboot. Once that was finished I rebooted  andused 

apt-get install ubuntu-desktop

It crashed and I had to rerun dpkg --configure -a 

3 different reboots to get it all working but it works fine once installed.  I think part of my problem may have been some bad memory.

---

### Post by paul7458 on 2006-12-27
[FONT="Fixedsys"][/FONT][COLOR="Purple"][/COLOR][LEFT][/LEFT
I have read you must click on the "install" icon on the ubuntu desktop. I do not have a cd burner so I can't use the alternate cd. I wonder if anyone could make one for me?

---

### Post by linear on 2006-12-27
> **paul7458 said:**
> I fixed the video. I have an arrow on a brown screen then several hours later all I have is a purple screen with no arrow. And yes the hard drive is still spining. Oh it's a grape imac dv. Other than the xorg settings is there anything I missed?

1. Are you certain you disabled dri in xorg.conf?

2. Have you checked for the [Date Bug]("https://help.ubuntu.com/community/UbuntuDateBug")?

---

### Post by paul7458 on 2006-12-27
I did disable DRI and my date is right.

---

