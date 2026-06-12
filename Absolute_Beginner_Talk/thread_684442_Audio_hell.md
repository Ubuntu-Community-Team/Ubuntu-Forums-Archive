---
title: "Audio hell"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Rhift on 2008-02-01
so it's been days and i have spent hours working on this and still nothing
I have a Vaio FZ180e 
 lspci -v says
 "Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller"
 aplay -l
says no sound card found

I have uninstalled and reinstalled alsa using several guides i have found for the FZ180 and still no luck

and yes i have added 
options snd-hda-intel model=vaio
to 
/etc/modprobe.d/alsa-base

if i click 
and try to test i get the following error
"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing."

any ideas

---

### Post by swoll1980 on 2008-02-01
go to system>adminastation>users>groups>alsa>properties add your self to the alsa group then you will be able to use it I think

---

### Post by oedha on 2008-02-01
may i ?
have you install linux-backports-modules-2.6.22.14-generic
and also install linux-backports-modules-generic_2.6.22.14

mmmmm........model=vaio...not sony ?
~E~

---

### Post by Rhift on 2008-02-01
thanks so much for the help! It's nice to have sound back

---

