---
title: "[SOLVED] Mic not working"
date: 2007-10-03
forum: Apple Intel Users
---

### Post by PaulFXH on 2007-10-03
Well, I thought I had Feisty working just perfectly on myMacBook (C2D, 2.16 GHz) until I tried to make a Skype call today and guess what: the mic doesn't work.
I've googled around and tested a bunch of things but no luck.
What particularly bothers me is that the sound test on System>Preferences>Sound>Devices>Audio Conferencing>Sound Capture (on Alsa, but I've tried all the others) gives no sound.
Would appreciate some advice.
Thanks
Paul

---

### Post by PaulFXH on 2007-10-04
I finally can use my headset microphone to make Skype calls in Ubuntu on my MacBook (note that Skype has always worked perfectly in OS X on this machine without doing any configuration at all).
All the changes I made were in Gnome-Volume-Control (rt click on volume icon and choose Open Volume Control) and then

1) Open Edit>Preferences and check everything
2)Under the Playback tab, unmute everything and make sure everything is turned up (adjust PCM and Front to control volume and bass to your taste)
3)Under Recording tab, unmute everything and turn up everything
4) Under the Switches tab, check everything EXCEPT FOR Mic as Output which should remain unchecked
5) Under the Options tab, Input Source should be set to Mic

This worked fine for me and despite it seeming a little obvious in retrospect, it took me quite a while to stumble on it.

---

### Post by jslmg on 2007-11-11
Paul, what would be the right audio settings in Skype itself?

---

### Post by MichaëlVD on 2007-11-12
I tried this on my iMac, but still no progress. I should probably just try harder, and try the suggestions cyberdork33 gave me once. Not today though...

---

### Post by jslmg on 2007-11-12
> **MichaëlVD said:**
> I tried this on my iMac, but still no progress. I should probably just try harder, and try the suggestions cyberdork33 gave me once. Not today though...

Michael, could you lead me to cyberdork's suggestions? Are they in a thread on these forums? I'm trying to get my mic to work with skype on a Mac mini, Ubuntu 7.10

---

### Post by MichaëlVD on 2007-11-12
It's not on the forums I think, but I'm sure he doesn't mind if I post it here:

> There is an extensive bug report about the open source ATI driver and this machine (video card). We almost made it into gutsy, but no such luck.

If you install the version posted at the end of the bug, you shouldn't have any issues.

[https://bugs.launchpad.net/ubuntu/+s...ti/+bug/132716](https://bugs.launchpad.net/ubuntu/+s...ti/+bug/132716)


Can you let me know whether this works for you?

---

### Post by jslmg on 2007-11-12
> **MichaëlVD said:**
> It's not on the forums I think, but I'm sure he doesn't mind if I post it here:



Can you let me know whether this works for you?

Unfortunately, that link is dead. For shame!

---

### Post by MichaëlVD on 2007-11-12
Here is the link, restored in its full glory: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/132716](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/132716)

---

### Post by cyberdork33 on 2007-11-12
> **MichaëlVD said:**
> Here is the link, restored in its full glory: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/132716](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/132716)
I am a bit confused. This doesn't seem to have anything to do with that. That bug was related to a graphics issue on for Inspiron 5100. I really don't know how to get the Mic working. I have actually never gotten mine working myself. There are some posts about it in the forum somewhere though.

---

### Post by jslmg on 2007-11-12
Michael,

Did you mean to post this, maybe, to another thread--the one about desktop effects being disabled? Some guys over there are asking about just the sort of thing that bug report addresses:

[http://ubuntuforums.org/showthread.php?t=604807&page=3](http://ubuntuforums.org/showthread.php?t=604807&page=3)

In this thread, I'm looking for a fix to my external microphone needs. My desktop effects problems have been solved, for now.

---

### Post by MichaëlVD on 2007-11-12
Oops, you're right, this has nothing to do with it. I guess I shouldn't be posting from work!

Lack of memory + lack of concentration = loss of time for you and me... Sorry for that.

---

### Post by MichaëlVD on 2007-11-12
Is there a bug report for the iMac microphone? I searched 'imac microphone' on launchpad, and I only found a bug report about the 1999 iMac.

---

### Post by MichaëlVD on 2007-11-17
I filed a bug report here [https://bugs.launchpad.net/ubuntu/+bug/163297](https://bugs.launchpad.net/ubuntu/+bug/163297)

No idea what information would be helpful, so feel free to add to it if you have the same problem.

---

### Post by cyberdork33 on 2007-11-17
> **MichaëlVD said:**
> I filed a bug report here [https://bugs.launchpad.net/ubuntu/+bug/163297](https://bugs.launchpad.net/ubuntu/+bug/163297)

No idea what information would be helpful, so feel free to add to it if you have the same problem.

You need you give lots of information about your hardware. 

- lspci -vvnn
- cat /proc/asound/version
- cat /proc/asound/card0/codec#0
- amixer

you can make the output of these commands go to a file by using '>'

example:
```
sudo lspci -vvnn > lspci.txt
```

This will make a text file named lspci.txt that has all the output inside it. You can then post this to the bug.

Also, you microphone has nothing to do with your camera...

---

### Post by MichaëlVD on 2007-11-17
Thanks. Those are attached to the bug report now.

---

