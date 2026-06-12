---
title: "[SOLVED] HELP : for someone with a little linux knowledge this is probably easy to so"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by daimaru on 2007-11-03
i have a usb headset. sound works fine, i can use vlc, movieplayer, amarok no problems with sound. 
but when i watch flash videos in browser i got no sound same if i start Enemy territory Quake wars or zattoo player. 

to get sound with these apps i have to [COLOR="black"][COLOR="black"][COLOR="Red"]unplug my usb and reinsert it[/COLOR][/COLOR][/COLOR]. then sound works.
so my question is how can i tell ubuntu to always use that usb adress or whatever it is thats different from before unplugging and reinserting usb.

plz tell me which console commands to enter in order to give more info on the hardware stuff or whatever is happening with the usb. thx

---

### Post by mrvertigo on 2007-11-03
I'll look into this for you

---

### Post by Hendrixski on 2007-11-03
That's very strange.  So, your sound for flash videos stops working if you plug in something to your USB?  Is it just specific things that you plug into your USB or just anything?  Other sound continues to work though, it's just flash that stops?

And does this happen only after you've hibernated the computer?  Becuase I know that some computers have messed up acpi that makes the USB's not work after you hibernate it.

---

### Post by mrvertigo on 2007-11-03
mmm good point, I overlooked the notebook issues :P

---

### Post by daimaru on 2007-11-04
fist thank you for responding, i really need help on this. sry should have been more clear. I'm on desktop computer so no notebook problem. 
the Headset I'm using is a USB-Headset, so it does not need a soundcard. I have my motherboards onboard sound disabled, because the USB-Headset works without soundcard. 
Now sound works fine and everything its just that games and in this case i guess even flash uses a different hardware address or something. 

_as an example: _
When i open VLC Video Lan player and go to settings->preferences->audio->output modules->ALSA
it says there:
ALSA device name  [COLOR="Red"]**hw:1,0**[/COLOR]

this is when booting computer and having had the headset plugged in.

now if i pull out the USB-Headset and plug it back in VLC Player now shows 
ALSA device name  [COLOR="Red"]**hw:0,0**[/COLOR]

and now youtube videos in flash player work with sound, and games sound work too. 

so what I am asking is how can i BIND that address to my USB-Headset, so that it always uses this address and not a different one. 

hope this is enough info to work on. thanks

---

### Post by daimaru on 2007-11-05
bump. plz help

---

### Post by tony.morse on 2007-11-06
I have a very similar problem. Basically all sound works fine except for flash, oh and every now and again I have to change the prefs in XMMS.  I have a desktop machine with two sound cards, one on board and the other an audigy.  I use the audigy and not the onboard one.  Anyway I can't figure out how to tell flash to use the audigy, and it's a pain having to reconfigure XMMS every now and again.

This must be easy to solve, perhaps with a script setting the defaults up or something?

---

