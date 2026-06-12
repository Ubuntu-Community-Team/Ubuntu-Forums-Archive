---
title: "Macbook Pro Sound Buttons 8.04"
date: 2008-04-28
forum: Apple Hardware Users
---

### Post by guerramacina on 2008-04-28
Hey I put a fresh install of Hardy replacing my Gusty on my macbook pro. It is triple booted but that isn't my problem. I have searched around for this problem and haven't been able to find a solution. Whenever I try to control my sound with the sound keys nothing happens..the sound doesn't get louder or quieter, but the sound icon comes up and goes up and down but like I said nothing happens. Any help would be great.

edit: forgot to mention all the other keys work (brightness, keyboard lighting)

---

### Post by cyberdork33 on 2008-04-28
In system preferences, you need to set the correct channel to control to adjust your volume.

---

### Post by guerramacina on 2008-04-28
what exactly does that mean?

---

### Post by cyberdork33 on 2008-04-28
that means go into the system > preferences > sound

at the bottom of the window, you select the channel that your keyboard should control. It is obviously controlling the wrong channel currently. you can use 'alsamixer' in the termial to find the right channel.

---

### Post by undertakingyou on 2008-06-24
Sorry to reopen an old thread but I am having a similar issue that I can't resolve.  When I press the F4 or F5 (Volume up-Volume down respectively) it adjusts both the Master Channel and PCM.  I have tried to change that by doing several things.  First, I tried doing SYSTEM => PREFERENCES => SOUND and setting it to just the master.  Then I tried it by right clicking the volume applet on the panel and settings its preferences to that.  I also tried editing /etc/pommed.conf and telling it to do nothing with the volume buttons.  All to no avail.  

Second sound issue.  When I hit F3 (Volume Mute) it mutes both the master channel and the front speakers.  When I hit F3 again it only unmutes the master channel, leaving the front speakers muted and me with no sound.  All the above attempts did nothing to fix this.

If anyone has any insite I'd love to hear it.

---

### Post by cyberdork33 on 2008-06-24
> **undertakingyou said:**
> Sorry to reopen an old thread but I am having a similar issue that I can't resolve.  When I press the F4 or F5 (Volume up-Volume down respectively) it adjusts both the Master Channel and PCM.  I have tried to change that by doing several things.  First, I tried doing SYSTEM => PREFERENCES => SOUND and setting it to just the master.  Then I tried it by right clicking the volume applet on the panel and settings its preferences to that.  I also tried editing /etc/pommed.conf and telling it to do nothing with the volume buttons.  All to no avail.  

Second sound issue.  When I hit F3 (Volume Mute) it mutes both the master channel and the front speakers.  When I hit F3 again it only unmutes the master channel, leaving the front speakers muted and me with no sound.  All the above attempts did nothing to fix this.

The master channel usually doesn't adjust anything. It sounds like your problem is deeper than this, but I just wanted to make sure.

---

### Post by undertakingyou on 2008-06-24
When I adjust the sound I watch both the master and PCM channels adjust.  When I mute I watch both the Master and Front mute.  So, it is doing both on me.  And the sound seems to work just fine otherwise.  The real issue I believe comes down to the keyboard buttons.  

Does applesmc do anything to the keyboard at all?  Because when I comment out the audio sections in /etc/pommed.conf it doesn't change a thing.

Any pointers would really be appreciated.

---

### Post by cyberdork33 on 2008-06-24
i don't think that you need pommed for the volume keys.

---

