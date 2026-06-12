---
title: "microphone issues"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by yoma819 on 2008-04-08
i have recently been trying to get my microphone to work without any sucess!
when i use the team speak app to check my mic is working i just hear myself!
i have been advised to go onto the playback tab in the audio settings and mute the microphone
then look at the recording tab
the only problem is i dont have one!
i am using a realtech ALC861 
i would upload a print screen but i dont know how to do that!
thanks in advance
--yoma

---

### Post by Crafty Kisses on 2008-04-08
Does your headset require any drivers?

---

### Post by yoma819 on 2008-04-08
i dont think so
it is not usb
and under windows i never needed any!
it is just a normal mic jack
how would i check if they were needed?
thanks
--yoma

---

### Post by funfrank on 2008-06-05
I'm also having the same problem with an ALC861.  When I open volume control, I see oss mixer in parenthesis. This refers to the device. But for this device, I can only see one playback tab.  

Where are the other tabs?

Whilst searching for these tabs, I've tried changing the device in the file menu of the volume control applet. I have four selections (0,1,2,3): the oss mixer, alsa playback, alsa capture monitor source, and alsa capture. 

When I select one of these devices, for example, alsa capture, I can see another tab, for example recording, but never within the mixer. Worse, any adjustment (un-muting, volume increase, etc.) does nothing for my dead microphone. Fiddling with system->preferences->audio gets me nowhere, either. 

When I edited the /etc/modprobe.d/alsa-base according to this article: 

[http://ubuntuforums.org/showthread.php?t=616845&highlight=realtek+alc861+microphone](http://ubuntuforums.org/showthread.php?t=616845&highlight=realtek+alc861+microphone) 

my speakers died, too. 

Any suggestions?

___________________________________________
Toshiba Satellite A105-s2031 Hardy 8.04

---

### Post by slaming on 2008-06-30
having the same issues but using a cnet or sumin usb headset working fine but not with ts waaaaaaaaaaaa
i miss my squad mates!

---

