---
title: "Want to help a Newbie enable multi-touch in 9.04?"
date: 2009-05-09
forum: Apple Hardware Users
---

### Post by joshmaker on 2009-05-09
After hearing lots of great things about Ubuntu 9.04 I thought I would give it a try.  While things seem much smoother and easier than the last time I played around with Linux a year or two ago, the track pad on my new unibody MacBook Pro is almost unusable.  

I found this thread: [http://ubuntuforums.org/showthread.php?t=840040](http://ubuntuforums.org/showthread.php?t=840040) on adding Multi-touch support, I haven't had much luck as I am pretty inexperienced with linux.

Following the directions i found online, here is what I have done so far:

I opened /etc/apt/sources.list and added
deb [http://ppa.launchpad.net/mactel-support/ubuntu](http://ppa.launchpad.net/mactel-support/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/mactel-support/ubuntu](http://ppa.launchpad.net/mactel-support/ubuntu) jaunty main

Then, in the terminal I ran:
sudo apt-get update
sudo apt-get install bcm5974-dkms

As far as I could tell everything seemed to install correctly.  

Then, using the terminal I ran
sudo gedit /etc/X11/xorg.conf 

and I pasted in the settings I found at [http://bitmath.org/code/bcm5974-dkms/xorg-settings-without-tapping.html](http://bitmath.org/code/bcm5974-dkms/xorg-settings-without-tapping.html) onto the bottom of the file.

After that, I ran out of directions so I tried logging out and back in again, however I could't see any changes in my tackpad.  Can anyone give me a suggestion as to what to do next?

---

### Post by apparle on 2009-05-09
After you logged out did you try "Restart X Server" option.......if that also doesn't work try to see if restart works

---

### Post by inphektion on 2009-05-09
You used a bit of older info...

follow this and it'll work perfectly:
[https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty)

---

### Post by joshmaker on 2009-05-09
Thanks for the help, I'll give it a try

---

### Post by joshmaker on 2009-05-09
Well, everything installed correctly, but I still need to work on my settings.  Right clicking and the two finger scroll work, but the suggested settings listed here: [https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty#Touchpad](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty#Touchpad) won't let me click and drag anything.

Does anyone have a working .fdi file they could share with me?

---

### Post by andrewenoble on 2009-05-10
Ignore this.

---

