---
title: "Gnome won't remember my refresh rate"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by 4KvRMU7Nnv on 2007-09-22
Ok.  this is really weird but I can't explain why it is happening.  I have an Nvidia card and, using nvidia-settings, I set the optimum refresh rate my card could handle.  I clicked apply and it applied it perfectly.  I looked in the "screen resolution" dialog of gnome and saw that the refresh rate was a nice 68 Hz.  I thought "good, thats the right speed".  When I rebooted the system, however, it went back down to 50 Hz.  In order to get the right refresh rate I have to change it in nvidia-settings each time!  I would definitely not like to do this and would appreciate any help I can get!  Thanks!

---

### Post by overdrank on 2007-09-22
> **d3br074 said:**
> Ok.  this is really weird but I can't explain why it is happening.  I have an Nvidia card and, using nvidia-settings, I set the optimum refresh rate my card could handle.  I clicked apply and it applied it perfectly.  I looked in the "screen resolution" dialog of gnome and saw that the refresh rate was a nice 68 Hz.  I thought "good, thats the right speed".  When I rebooted the system, however, it went back down to 50 Hz.  In order to get the right refresh rate I have to change it in nvidia-settings each time!  I would definitely not like to do this and would appreciate any help I can get!  Thanks!

Hi I believe you have to open nvidia settings in sudo like this 
```
sudo nvidia-settings
``` then it will save your settings 
Hope this helps good luck!

---

### Post by 4KvRMU7Nnv on 2007-09-23
yes this worked although I actually figured it out already.  This verifies that I did the right thing.  Thanks

---

