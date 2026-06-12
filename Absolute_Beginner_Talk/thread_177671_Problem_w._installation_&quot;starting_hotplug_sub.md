---
title: "Problem w. installation &quot;starting hotplug subsystem&quot;"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by Andreas Johansson on 2006-05-16
Hi!

Earlier today I tried to install Ubuntu on my FujitsuSiemens M1467. Since I wanted to keep XP I put it on a partition. Everything went well until re-booting the system. Ubuntu loaded until "starting hotplug subsystem", then it just stopped and left a cursor blinking (not frozen but not really possible to do anything earlier). 

Now, I have made searches on the forum and found other users sharing the similar problem, which obviously seem to be related to graphic card incompability. The only thing I got from those post was that I should press ctrl + C right before "starting hotplug subsystem" was loaded. I did and my computer continued booting. However, I never got Ubuntu to load. Instead it stopped at another instant, showing a grey screen with different commands on it. 

If anyone has an idea what to do with this please let me know. I would really like to try Ubuntu out. Do let me know if you need additional information on hard- or software.

Best regards

Andreas Johansson

---

### Post by skinnygmg on 2006-05-16
what kind of graphics card?

what were the commands on the grey screen?

---

### Post by Andreas Johansson on 2006-05-16
[QUOTE=skinnygmg]what kind of graphics card?

Thanks for your reply. I have a ATI Mobility Radion X700.

what were the commands on the grey screen?[/QUOTE]

I tried to get to the same screen again but failed. I managed to skip the hotplug but instead ended up with "Starting PCMIA services" as the last command. Same thing, loading Ubuntu is halted but not frozen. 

Got a fail on "Synch clock to utp.ubuntu.linux.org", which is because I didn't use a network cable but my wifi - obviously not loaded at the time. Could that have any effect?

---

### Post by skinnygmg on 2006-05-16
no.  i use a wifi connection, and my synch clock fails every time, but no other issues

---

### Post by Ptero-4 on 2006-05-16
Do a ctrl-C on "Starting PCMCIA services". That will probably let you through a bit further. And as for your two errors, they are this: The hotplug one is about the linux "plug & play" enabler (hotplug) and the second is about problems with the PC Card (PCMCIA) slots. It may be that the drivers for your PC Card slots aren't working or installed at all and the PC Card subsystem fails to load making hotplug fail also.

---

