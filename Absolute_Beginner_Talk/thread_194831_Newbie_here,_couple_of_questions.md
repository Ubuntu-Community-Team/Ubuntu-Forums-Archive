---
title: "Newbie here, couple of questions"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by jISh on 2006-06-12
Okay, I've installed this. First Linux distro I could get my DWL-G122 adaptor to work properly on :) 

Just a couple questions come to mind right now, 
a) I have my DWL-G122 (rev a2) working with ndiswrapper and the official drivers from the CD, the only thing is I have to "sudo modprobe ndiswrapper" every time I reboot the computer, in order to enable the proper driver. Any way to make it work automatically?
b) How can I make Gaim (the instant messenger) start automatically? I see no option like there was in the Windows build.

Thanks, if I have any further questions as I experiment with this Linux I will add to this thread.

---

### Post by Titus A Duxass on 2006-06-12
You need to add ndiswrapper to /etc/modules and tailor your /etc/network/interfaces file so that your wlan0 comes up auto.

Try using the wonderful search feature to get more info.

---

### Post by fer5437 on 2006-06-12
For start up gaim at the startup, what you need to do is when you configure account for gaim, there is option for you to save your password and auto-login. Just check these 2 option. Then go to System->Preference->Sessions->StartupProgram and add gaim to it.

---

### Post by Jagot on 2006-06-12
[QUOTE=jISh]
a) I have my DWL-G122 (rev a2) working with ndiswrapper and the official drivers from the CD, the only thing is I have to "sudo modprobe ndiswrapper" every time I reboot the computer, in order to enable the proper driver. Any way to make it work automatically?[/QUOTE]

After you've modprobed:

```
sudo ndiswrapper -m
```

---

### Post by jISh on 2006-06-12
Thanks guys, solved both of those small issues :)
Loving this distro :)

---

