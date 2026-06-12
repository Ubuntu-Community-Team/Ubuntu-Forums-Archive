---
title: "No Mic boost"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Malicious41 on 2007-06-20
Hello people I have been using Ubuntu for a while now, and I have a little problem. My Microphone is really low, and I read alot of post where it says to enable mic boost, but I don't have a mic boost option. I have ALSA, I think.. when I open volume control it says HDA nVidia (Alsa Mixer). I know when I ran Windows I used the RealTek AC97 Codec Drivers. When I install those divers and reboot I get this error

> Your session only lasted less than 10 seconds. Error while loading shared libraries: libasound.so.2 cannot open....etc etc

So any idea on how I get Mic Boost?

---

### Post by Happy_Man on 2007-06-20
How did you get Windows drivers to install under Ubuntu?

---

### Post by adamklempner on 2007-06-20
Open a terminal and type:
```
alsamixer
```
Use the arrow keys to highlight "Mic Boost" and press "m" to turn it on.  That should do it. 

You can also adjust capture volume levels while you are in there.

---

### Post by adamklempner on 2007-06-20
Also, the AC97 drivers should have come with Ubuntu as that sound chip is very well handled in Linux.  If you installed some other drivers, it might be good to try to uninstall them and get the native Ubuntu ones to work.

---

### Post by ronmarley1 on 2007-06-20
Another option, if you don't want to use the terminal method, would be to double click on the volume icon on the top panel.  Then, click on Edit ->Preferences.  Under "Select tracks to be visible:"  click the box in front of Mic Boost (+20dB).  That will create a new tab called "Switches."  Close the preferences box and click the Switches tab and then click the check box for Mic boost.

---

### Post by Malicious41 on 2007-06-20
So yeah I tried doing that, but there is no mic boost option, I should have mentioned that's what I ment in the beginning. Here is a screenshot, not Mic Boost

[http://i179.photobucket.com/albums/w288/Blank41/Screenshot7.png](http://i179.photobucket.com/albums/w288/Blank41/Screenshot7.png)

---

### Post by Golyadkin on 2007-06-20
I have a similar problem, only for me the thing shows up as both (SB Live 5.1) ALSA mixer and (eMicro EM28028)....

---

### Post by Malicious41 on 2007-06-20
Anyone?

---

### Post by Malicious41 on 2007-06-20
Bump

---

### Post by carloslosgrande on 2007-06-20
Ok, in alsamixer you can hit the 'tab' button to get extra functions.........or.........as ronmarley1 said  click on the volume icon and you should get a gui to play around with all of the options

---

### Post by gints on 2008-02-23
still there is no boost option at all

---

### Post by carloslosgrande on 2008-02-24
[FONT="Comic Sans MS"]I also have no 'boost' option but I do have a volume slider for each.
In the volume icon - double click and tick all the relevant boxes under 'edit' > 'preferences'
Move the sliders under 'record' to the top and make sure the mic isn't muted. there should be at least 2 - 'capture' and 'mux'.
play around and see what changes you get.
Also I set my  'options' to 'front mic'
Hope this helps.

Oh, its better to start your own thread, you'll get more replies.[/FONT]

---

### Post by mogwai on 2008-03-26
have you seen this: [http://ubuntuforums.org/showthread.php?t=118916]("http://ubuntuforums.org/showthread.php?t=118916")

---

