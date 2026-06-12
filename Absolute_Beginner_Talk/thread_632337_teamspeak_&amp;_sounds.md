---
title: "teamspeak &amp; sounds"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by gunhippy on 2007-12-05
Installed Teamspeak from the Repositories with no problems, loads fine and can connect to servers fine.

However when i connect my mic and headset are muted by default, i don't hear any voices or program sounds (like that sound clip of the chick saying you're connected).

If i try to unmute either inside ts nothing happens.

I had a look around, and read some stuff about alsa-oss. Using a guide i installed it, and ran Teamspeak with 'aoss Teamspeak', after doing that i connected and my mic and headset where unmuted. However, i was still hearing no sound, and hitting my bound key to let me speak didn't seem to do anything - the little green light didnt come on, nor could anybody hear me.

As far as i can tell, my settings in the volume controls are all good, i can record into the Ubuntu sound recorder just fine (though with aoss it just crashes sound recorder?), and whilst teamspeak is running with no sounds my music player will still run fine if i load it up. 

My headset isn't usb, just the regular one wire in my sound output hole and one to the mic in hole.

Any help would be appreciated

-andy

---

### Post by gunhippy on 2007-12-06
=[

---

### Post by LarPo on 2007-12-07
I'm not sure if this works for you, but I had to change Settings-> Sound Device from Default to /dev/adsp.

---

### Post by gunhippy on 2007-12-08
No change =[

That was set as default, i also tried manually setting it and it's all the same

thanks for the reply

---

### Post by gunhippy on 2007-12-13
:c

---

### Post by gunhippy on 2007-12-25
One last bump before i try elsewhere, i'd really liek to get this working >_<

---

