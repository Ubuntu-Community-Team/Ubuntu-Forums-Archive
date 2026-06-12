---
title: "Problems with Sound and Video after install"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by Squirrel Ninja on 2007-11-16
Whats up everybody
I just installed ubuntu studio, I really like it but I've got some problems I could use some help with.

First of if I don't activate my graphics card drivers, the video works, but when I do, the resolution gets really low and I get the message, Failed to connect to socket /tmp/dbus-1XrZb5G63z: Connection refused
The card is a nevida GeForce 8600M GT and I installed the drivers threw the restricted drivers manager, if you would recomend just not using it, I don't think that would be a huge issue.

Secondly, and more pressingly, I have no sound the volume controll brings up the message
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

I've seen other threads that talk about a simmilar issue, but I don't really understand what it is there asking, so please tell me what it is you want me to do, and how to do it.

Thanks a bunch
SN

---

### Post by Squirrel Ninja on 2007-11-16
*bump* come on little help

---

### Post by Sims2789 on 2007-11-16
For sound, try this:

Go to System -> Preferences -> Sound. This is what I did in Ubuntu, so I don't know if it's the same in Ubuntu Studio. Chances are, you want to select *ALSA mixer* under Default Mixer Tracks. Then, select the correct device from the list and make sure it's highlighted. I don't know which one's the right one for your computer, but on my laptop it's PCM.

If this doesn't work, go into the Volume Control by right-clicking on the speaker in the top menubar and make sure the Speakers checkbox under the Switches tab is checked. Under the Playback tab, make sure the volume isn't muted.

---

