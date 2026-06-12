---
title: "Sound Blaster replacement"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-07-02
I just changed my sound card for another.  One Sound Blaster for a Sound Blaster Audigy LS.

I cannot get it recognized by the applications and I do not understand why not.

asoundconf list
 gave me the following - 
Names of available sound cards:

ICH5

CA0106

SAA7134

Since ICH5 is the on-board card I set CA0106 to the default.

The list in Device Manager identifies the sound card in the section head as SB Audigy LS  and identifies it as Audigy SE (SB0570) and the value CA0106 is listed.

If I play the test sounds in skype I can hear them.  However, I cannot hear an incoming ring and people cannot hear me.

But that is about as far as it goes.   Alsamixer  reports alsamixer: function snd_ctl_open failed for default: No such device
.  Audacity does not show any activity when attempting to record from a mic and XMMS plays a stream from Streamtuner but no sound is heard ...

Any suggestions appreciated  of how to diagnose this?

---

### Post by expatCM on 2007-07-02
Ok ... part solved .... part not.

The easy bit is when making changes to default sound card settings ....  then **do it as root and the changes are saved**.  Ok .. my error.  This in turn means that alsamixer then works :)   So in turn is xmms ...   just a matter of adjusting the correct slider ....

But my problem now is that the master volume control appears in the system tray as muted.  If I right click I cannot un-mute it.  This does not stop the sound though ...  it appears to be disjointed from the sound settings.  I do not have any easy master control though ...

The other problem is that I cannot work out how to get the microphone / audacity to record.  I guess this will also be the same in skype but I have not yet been able to test.

---

