---
title: "Having problems playing music"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by Ioosef on 2007-08-08
I have a couple of problems playing music. When I insert the cd, a program called sound juicer starts up, and when I press play an error pops up that says, 

> 
Error playing CD.

Reason: Could not establish connection to sound server


and it doesn't play. 
Also, next to the clock there's the volume control, but when I try to open the 'volume control' another error pops up saying 

> 
No volume control GStreamer plugins and/or devices found.


Now, would all of the be caused by a crappy computer or because I'm missing some programs and such?

---

### Post by Al3xK3aton on 2007-08-08
Is this CD burned or legit?

---

### Post by Ioosef on 2007-08-08
burned...

---

### Post by amazingtaters on 2007-08-08
Looks like you need to install GStreamer. Look in synaptic for the files you need.

---

### Post by AlexenderReez on 2007-08-08
> **amazingtaters said:**
> Looks like you need to install GStreamer. Look in synaptic for the files you need.

for easiest way --->

> sudo apt-get install gstream*

---

### Post by tille on 2007-08-08
> sudo apt-get install gstream

is what u need dude

---

### Post by Ioosef on 2007-08-08
Thanks.
Now... this may sound kinda stupid, but... what exactly do I do with that? 
I'm kinda new to Linux.

---

### Post by dhtseany on 2007-08-08
> **Ioosef said:**
> Thanks.
Now... this may sound kinda stupid, but... what exactly do I do with that? 
I'm kinda new to Linux.

The **apt-get install** command installs the app and your good to go. You may have to reboot with this not being previously installed though

---

### Post by RomeReactor on 2007-08-08
Hi. You can run that command by opening a terminal (Applications->Accessories->Terminal); paste it there, then press enter. However, that command will install **a lot** of packages, including some that you won't need. Try installing these instead and see if that solves the problem:
```
sudo apt-get install gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-fluendo-mpegdemux gstreamer0.10-gnomevfs gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-mutiverse gstreamer0.10-plugins-ugly plugins-ugly-multiverse
```

---

### Post by dhtseany on 2007-08-08
Sorry, just re-read your question:

Open a command prompt (under Applications -> Accessories)

Type the following:
```

$sudo apt-get install gstream
Password: The password for your account

```

The apt-get install will literally install gstream for you.

Hope this helps

---

### Post by amazingtaters on 2007-08-08
Open up Terminal (Applications > Accessories > Terminal) and type in the command (sudo apt-get gstream*) and it will download and install all gstream files that you need.

Edit: Ahh beat to it, and Rome's instructions are better...

---

### Post by Ioosef on 2007-08-08
Thank you for your help everybody... but it still doesn't work... but i got this message afterwards, although I don't remember what I did.

> 
The volume control did not find any elements and/or devices to control. This means either that you do not have the right GStreamer plugins installed, or that you do not have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.


---

### Post by dhtseany on 2007-08-09
Then that sounds to me like your sound card wasn't detected. Can you give some details on the card? (Make, model, onboard/PCI, etc.)

---

