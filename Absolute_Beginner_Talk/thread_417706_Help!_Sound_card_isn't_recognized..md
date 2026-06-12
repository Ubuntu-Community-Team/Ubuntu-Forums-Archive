---
title: "Help! Sound card isn't recognized."
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by gibsongirl on 2007-04-21
My sound card isn't recognized by Ubuntu 6.06. I am not techy by nature, but I wanted to get away from windows os's (sp?).  I have a Cs4235 sound card, and I don't understand how to get Ubuntu to use it. There is also a problem with using ALSA, there is an error. :confused:  Other than that, this is a wonderful Os.  I have been recommending it to my friends.  I would greatly appreciate any help you can give me.  Thanks for your time and knowledge.  :KS

---

### Post by leibowitz on 2007-04-21
It is totally normal, as you seems to have an ISA card (by Cirrus Logic) and they need to be configured manually to avoid shared IRQ conflicts.

To configure it, you will need to load a kernel module. I don't have this card, so I don't know exactly what options it needs. So maybe your system will becoming unstable. If it is, then you just need to restart the computer to forget the configuration. 

To do that, go to the Applications menu, Accessories, Terminal, and paste this command into it.

```
sudo modprobe snd-cs4236
```

If it succeed, then you will see no output message. It you have any message, please paste it here (it will probably say it needs more options to load it)

PS: this operation will not be saved upon reboot of the computer. This is voluntary. It's just for testing purpose. In case of success, the name of the kernel module (ie: snd-cs4236) should be added to the "/etc/modules" file, by doing this:

[COLOR="Red"]Warning:[/COLOR] do this only if the previous command has resolved your sound configuration !
```
gksudo gedit /etc/modules
```
And add a line in the end of the file, with only this:
```
snd-cs4236
```


More information here: [https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)

---

### Post by overdrank on 2007-04-21
> **gibsongirl said:**
> My sound card isn't recognized by Ubuntu 6.06. I am not techy by nature, but I wanted to get away from windows os's (sp?).  I have a Cs4235 sound card, and I don't understand how to get Ubuntu to use it. There is also a problem with using ALSA, there is an error. :confused:  Other than that, this is a wonderful Os.  I have been recommending it to my friends.  I would greatly appreciate any help you can give me.  Thanks for your time and knowledge.  :KS

Hi try and go to system preference sounds and make sure it is set as the default sound card. good luck:popcorn:

---

### Post by gibsongirl on 2007-04-21
Thank you so much,  i can hear!  It is really quiet but I can hear!  :D


> **leibowitz said:**
> It is totally normal, as you seems to have an ISA card (by Cirrus Logic) and they need to be configured manually to avoid shared IRQ conflicts.

To configure it, you will need to load a kernel module. I don't have this card, so I don't know exactly what options it needs. So maybe your system will becoming unstable. If it is, then you just need to restart the computer to forget the configuration. 

To do that, go to the Applications menu, Accessories, Terminal, and paste this command into it.

```
sudo modprobe snd-cs4236
```

If it succeed, then you will see no output message. It you have any message, please paste it here (it will probably say it needs more options to load it)

PS: this operation will not be saved upon reboot of the computer. This is voluntary. It's just for testing purpose. In case of success, the name of the kernel module (ie: snd-cs4236) should be added to the "/etc/modules" file, by doing this:

[COLOR="Red"]Warning:[/COLOR] do this only if the previous command has resolved your sound configuration !
```
gksudo gedit /etc/modules
```
And add a line in the end of the file, with only this:
```
snd-cs4236
```


More information here: [https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)

---

### Post by leibowitz on 2007-04-21
no prob :guitar:

---

