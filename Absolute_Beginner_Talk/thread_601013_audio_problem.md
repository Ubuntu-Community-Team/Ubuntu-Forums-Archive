---
title: "audio problem"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by a_satari on 2007-11-02
hi, I can't get my sound to work. Its not working at all. I'm using Ubuntu 7.10. I think my sound card is:

Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 03)

I'm new at ubuntu and it seem like I'm not patient enough solve this problem myself. Any help is welcome. 

Thank you.

---

### Post by philidox on 2007-11-03
I have the exact same audio card, if you find anything let me know

---

### Post by philidox on 2007-11-03
OMG!!! It was insanily easy to fix this issue!!!

Right click on the volume icon in the top panel. Choose “Open Volume Control.”

In the Volume Control,  select VIA 8237 if it’s not selected.

Select  Edit/Preferences in the menu, and on the dialog that pops up, checkmark “External Amplifier.”

Now Volume Control should have a third tab, “Switches.” The only setting on that tab is “External Amplifier,” a checkbox.  Uncheck the checkbox.  Volia!  Sound!

here is the url like

[http://www.goesping.org/archives/2006/05/13/ubuntu-sound-on-gateway-laptop/](http://www.goesping.org/archives/2006/05/13/ubuntu-sound-on-gateway-laptop/)

---

### Post by a_satari on 2007-11-03
Thanks philidox! The sound is working!! I spent hours trying to solve this problem. 

I couldn't find VIA 8237 but when I unchecked "External Amplifier" it worked !!

I have new faith in Ubuntu ...untill the next problem ;)

---

### Post by jeanatprev on 2007-11-15
Very new to Ubuntu, I have a Dell Latitude D830 Laptop, but the loudspeakers didn't work so far. When I read Philidox's answer I thought I had it, but unfortunately, when I try to open the volume control I have a message saying (approximately because I have a French version) "No plugin found for volume control GStreamer and/or peripheral". What I could find in the material identity under audio is: "82801H (ICH8 Family) HD Audio Controller". Can you tell me what is missing to make the loudspeakers work  :confused:
By the way, the USB head set is working all right.
Thanks for your patience !

IS THERE ANYONE ON THIS FORUM WHO CAN HELP ? i AM ADDING THIS ON 29.11.07

---

