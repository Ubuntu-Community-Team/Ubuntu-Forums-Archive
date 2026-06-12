---
title: "Sound Card Information"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by pavicnat on 2007-12-30
How do I find what soundcard my computer has? I need this information to fix a sound problem.

---

### Post by forestpixie on 2007-12-30
try using these in a terminal

```
lspci
aplay -l
```

---

### Post by tommcd on 2007-12-30
Run "sudo lspci -v" from terminal. This will tell list all hardware, including the soundcard. Scroll through it to find the soundcard. 
Run "lspci | grep audio" to just list soundcard. 
To find the modules being loaded run "lsmod". To just list the soundcard modules run "lsmod | grep snd".
See this for troubleshooting sound problem:
[https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28sound%29](https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28sound%29)

---

### Post by pavicnat on 2007-12-30
I used:
```

lspci
aplay -l
```

and I got: 
```

card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Modem [SiS SI7013 Modem], device 0: Intel ICH - Modem [SiS SI7013 Modem - Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

It seems to me that this is information for a modem, would that make my soundcard ICH. Also I have an AMD but it says Intel there, which confuses me.

---

### Post by tommcd on 2007-12-30
Run the lspci commands I listed in my last post. Especially the "lspci -v". That will list everything. Find the info about your soundcard and post it here. Also work through the troubleshooting guide I linked to.

---

### Post by pavicnat on 2007-12-30
```

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)

```

The reason I need the information is that I'm trying to return sound to my internet. I am using this guide: [http://ubuntuforums.org/showthread.php?t=455147](http://ubuntuforums.org/showthread.php?t=455147)

and my question is about this part of the code: 
```

cd alsa-driver-1.0.15rc3/
sudo make clean
sudo make mrproper
./configure --with-oss=yes --with-cards=hda-intel 
sudo make
sudo make install
```

my issue is what I should put instead of hda-intel

---

### Post by tommcd on 2007-12-30
Do you have backports listed in your sources.list? Open up synaptic and then the repositories and check and see if backports is enabled. According to this...
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119266](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119266)
...alsa 1.0.15 stable has been added to backports. Reload synaptic after adding backports (if not already enabled) and check for updates with update manager (close synaptic first).

---

### Post by pavicnat on 2007-12-30
I was able to fix the problem, it's fine now. Thanks for the coments.

---

