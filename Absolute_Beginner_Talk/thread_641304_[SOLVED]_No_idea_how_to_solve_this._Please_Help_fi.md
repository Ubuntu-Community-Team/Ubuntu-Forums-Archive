---
title: "[SOLVED] No idea how to solve this. Please Help fixing my sound device!!"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by daimaru on 2007-12-15
ok I've been trying to solve this for some time, but no success. Please check the screenshots to see what i mean, which saves me the lengthy explantions.
I'm using a USB-Headset, so no built in sound card in the pc. 

the noSound.jpg shows that my alsa.card device is at 1 (0x1) and the withSound.jpg shows it at 0 (0x0).

When my system starts (from fresh reboot) the alsa.card is set to 1 (0x1) and i have no sound. Then I unplug (pull out the usb cable) my USB-Headset and reinsert it. Which makes my alsa.card show up on 0 (0x0) and now I have sound \\:D/.

you may thing so what... but in order for me to have sound using firefox flash or mplayer the device has to be at 0 (0x0) and not 1 (0x1). otherwise i do not get sound. 

**what i need is a way to tell ubuntu to always start my sound device on the 0 (0x0) right from boot-up **. I have absolutely no idea how to do this. :confused:

please help [-o<

---

### Post by eggdeng on 2007-12-15
Try
```
sudo asoundconf list
```
to get the names of available cards. Then
```
sudo asoundconf set-default-card name_of_card
```

---

### Post by daimaru on 2007-12-15
well will that help with the hardware address it uses? i mean its not that i have 2 soundcards and i need to set one to use as default. anyways ill reboot in a sec, but the list command shows only 1 card , so i guess this won't work. 

```
sudo asoundconf list
Names of available sound cards:
Headset

```
EDIT: just rebooted. didn't work :( alsa.card is again at 1 (0x1)

---

### Post by Pumalite on 2007-12-15
What about:
lshw -C sound

---

### Post by daimaru on 2007-12-15
lshw -C sound 
gives me no output at all. I am using USB-Headset heres a [link]("http://www.amazon.com/Sennheiser-Traditional-PC-USB-canceling/dp/B0001MHYK6")  to clarify. no sound card is needed with the headset, because it has a built in one or something.

my headset and sound works in ubuntu and all, the only thing is that i want to change the hardware address to use 0,0 and not 1,0

---

### Post by Pumalite on 2007-12-15
Post then:
lshw
To know what your motherboard has.
(copy and paste)

---

### Post by daimaru on 2007-12-15
hey thanks, but i solved it (partially) 
i edited my 
/etc/modprobe.d/alsa-base
and commented out the option usb-audio. because as it happens usb-audio and other devices are by default prevented from grabbing address 0.
thats all fine and now my sound works (even with mplayer - which was the main reason i wanted to fix this) 
but i now have a new weird problem. if i start player from terminal everything seems to work fine. but if i start mplayer by rightclicking a file and oopening it with mplayer or by starting mplayer gui and dragging a file on there, i get this error message popping up in  a millisecond interval...
```
alsa-control: unable to find simple control 'PCM',1
```
that is displayed in a popup box. I'll add a screenshot.

the error popup box behaves like a strobe popping up very fast and fading into background again :confused::confused::confused:
this is soooo weird .

---

### Post by daimaru on 2007-12-15
nevermind i change output in mplayer to OSS and the popup is gone. that works for me . thanks to everyone this thread is solved.

---

