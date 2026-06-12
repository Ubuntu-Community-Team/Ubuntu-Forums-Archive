---
title: "apt-get install [RadeonHD 2600 drivers 10.10 PPC G5]?"
date: 2010-10-04
forum: Apple Hardware Users
---

### Post by Jason Argonaut on 2010-10-04
When I upgraded my 2004 Apple G5 PPC tower from 10.04 lucid to 10.10 server the ATI RadeonHD 2600 video drivers got bonked.   I can only get the command line.  Any help?   (sudo apt-get install ???) Thanks. --JA.

---

### Post by zeroti on 2010-10-04
what's the result of:

```
apt-cache policy xserver-xorg-video-radeonhd
```if it's not installed, you could always try the following:

```
sudo apt-get install xserver-xorg-video-ati
```or maybe to be more specific:

```
sudo apt-get install xserver-xorg-video-radeonhd
```Are you sure it's the drivers that aren't working?

---

### Post by Jason Argonaut on 2010-10-05
> **zeroti said:**
> what's the result of:

```
apt-cache policy xserver-xorg-video-radeonhd
```if it's not installed, you could always try the following:

```
sudo apt-get install xserver-xorg-video-ati
```or maybe to be more specific:

```
sudo apt-get install xserver-xorg-video-radeonhd
```Are you sure it's the drivers that aren't working?
Response from the 1st apt-cache is "none".
Response from the video-ati command is "already newest version."
Response from the 3rd command is "no such package".

Now what?
--JA

---

### Post by zeroti on 2010-10-05
I'm not really knowledgeable in this area. Are you getting any errors on bootup? I'm not really sure which logs to look at, but I'm curious...

what's the output of:

```
/var/log/Xorg.0.log
```You could always try the live cd to see if it starts up. And then you could diagnose the problem from there. It would require less technical experience to copy the logs into this forum in this way, (by copying them from the mounted hard drive that's hosting the problematic installation). An alternative is to mount a flash drive from the command line using your current installation, and copying over the log. You could also try browsing on your computer and searching for errors with the following command, and then posting them online using another computer:

```
less /var/log/Xorg.0.log
```Then type at the colon symbol:

```
/(EE)<return>
```that will search for instances of (EE). then type / and enter again to jump to the next one.

you could also try installing "links", a text-based web browser, if you have internet access on that machine:

```
sudo apt-get install links
```Good luck!

---

### Post by linuxopjemac on 2010-10-06
I think the problem  resides in your xorg.conf file.

What is the monitor that you are using ? Specs please.

---

### Post by Jason Argonaut on 2010-10-06
> **zeroti said:**
> I'm not really knowledgeable in this area. Are you getting any errors on bootup? I'm not really sure which logs to look at, but I'm curious...

what's the output of:

```
/var/log/Xorg.0.log
```You could always try the live cd to see if it starts up. And then you could diagnose the problem from there. It would require less technical experience to copy the logs into this forum in this way, (by copying them from the mounted hard drive that's hosting the problematic installation). An alternative is to mount a flash drive from the command line using your current installation, and copying over the log. You could also try browsing on your computer and searching for errors with the following command, and then posting them online using another computer:

```
less /var/log/Xorg.0.log
```Then type at the colon symbol:

```
/(EE)<return>
```that will search for instances of (EE). then type / and enter again to jump to the next one.

you could also try installing "links", a text-based web browser, if you have internet access on that machine:

```
sudo apt-get install links
```Good luck!
Thanks zeroti & opjlinux, I became fed up with Server edition & reinstalled Desktop 10.10.  During Xserver installation a message flashed past about x.conf file being updated by manufacturer.   Now video display works great.  Many thanks.  This issue is closed.  -- JA

---

