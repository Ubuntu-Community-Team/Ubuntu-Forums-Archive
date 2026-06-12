---
title: "[SOLVED] HP laptop sound card problem"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by wiktor91 on 2008-02-02
Hey i recently installed Ubuntu on my HP nx9010 laptop and with minor problems i got flash player installed. But when i look at videos on youtube or when i try to listen music there is no sound. 

There is a warning on Volume control that i don't have sound card configured or gstreamer plugins. I installed ALL gstreamer plugins that i have found but that doesen't fix the problem. So i guess that my sound card need a driver or something. Where can i find the driver for Ubuntu? The notebook is HP nx9010. 


And by the way where can i find drivers for toshiba bluetooth usb device? On CD that i got with it i only got Windows driver...

---

### Post by spiderbatdad on 2008-02-02
could you post the result of the ```
asoundconf list
```

Assuming you get a parameter like ICH82802ICH3 (just an example) You can run the command```
asoundconf set-default-card PARAMETER
``` where PARAMETER is the value from the previous command. Then reboot your system...after login, you should receive a notification as to the change.
If you do not get a real parameter from asoundconf list, right click on the volume applet and select preferences. See if there is another choice in the drop down selection box.

---

### Post by wiktor91 on 2008-02-02
I tried this and it doesen't work... 

But now i remember that when i instaled linux before 2 days i had sound imediately. When i loged in first time the welcome sound was playing. After that i didn't try to play any music, i tried it when i created new account and than it wasn't working. 

So maybe i screwed up something?

---

### Post by wiktor91 on 2008-02-02
Names of available sound cards:
A5451

This is result of asoundconf list command...

---

### Post by wiktor91 on 2008-02-02
Does anyone knows how to solve the problem?

---

### Post by spiderbatdad on 2008-02-02
check that Master and PCM are not muted in volume control. Logged in as the new user.
Signing out for a while...good luck.

---

### Post by wiktor91 on 2008-02-02
When i try to open Volume control i get a message

No volume control GStreamer plugins and/or devices found

---

### Post by wiktor91 on 2008-02-02
Problem solved...
When i was creating new account i did not alow myself to use Audio devices

---

