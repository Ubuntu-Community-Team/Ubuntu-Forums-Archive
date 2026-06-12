---
title: "Help no sound too"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by Lutte on 2007-02-07
Hello I have just installed the Kubuntu 6.10 Edgy, on my computer
- CPU: AMD64
- Soundcars: OnBoard VIA Technologies, Inc. VT8299/A/8235/8237 AC97 

The install worked fine, but there is no sound at all, even the start sound is not there.
I have allready asked for help in the german forum, but nobody can help me there.
My hope lies in this forum, if I can not handle this problem I have to go back to Windows, what I realy do not want to.

Everything seems to be ok the sound card is found and Amarok is playing everything. For Amarok everything seems to be fine, but there is still no sound.

aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: V8237 [VIA 8237], Gerät 0: VIA 8237 [VIA 8237]
Untergeordnete Geräte: 4/4
Untergeordnetes Gerät '0: subdevice #0
Untergeordnetes Gerät '1: subdevice #1
Untergeordnetes Gerät '2: subdevice #2
Untergeordnetes Gerät '3: subdevice #3
Karte 0: V8237 [VIA 8237], Gerät 1: VIA 8237 [VIA 8237]
Untergeordnete Geräte: 1/1
Untergeordnetes Gerät '0: subdevice #0

gives me this output, I do not understand at all. (Sorry for the german screenshot, but this is what I have)

Under XP everythng works fine.

---

### Post by ^rooker on 2007-02-07
It seems like your VIA soundcard identifies itself to the system as 2 different devices.
Have you configured which one is supposed to be used as default one?

What does "asoundconf --list" output?

---

### Post by ComplexNumber on 2007-02-07
**Lutte**
if you don't have the volume control applet on your panel, right click on the panel, select 'add to panel', choose the volume control and 'add'.
if you have the volume applet on your panel, right click on it and select 'open volume control'. check that there isn't any volume controls muted. 
also go to the 'File' in the menu and select 'change device'. is the correct device selected?

---

### Post by laidback on 2007-02-07
Have a look in System>Preferences>Sound.

In there you will find 3 tabs (2 in 6.06) the second one of which provides some sound testing.
If you have more than one device they will be listed in the drop down at the bottom of the screen, check that you have the correct one selected.
At the top of the screen is a list called **Select Check Box**, in here you can select a sound, say **Log on**, and get the system to play it straight away by pressing the right arrow key next to the drop down. Any sound? Put your ears close to the speakers as there may be a very low sound.

Another correspondent had this problem and installed a PCI card to determine whether sound was at all possible, turns out that there was a hardware fault on the mobo.

You will not need to go back to XP.

---

### Post by Lutte on 2007-02-07
thanks for the help, but the problem still exists.

rooker: asoundconf list
Names of available sound cards:
V8237

ComplexNumber: There is Mixer KMix installed, with a lot of swiches and sliders, i tried to switch them all on and bring them to maximum, but nothing.

laidback: Thanks for the help but I did not found the programm, but somthing simular, may be its the same. As my system is in german the names my differ.

I allready tried alsamixer, but to tell the truth there are some many possibilities to change something, that I do not not know what I have changed.

---

### Post by laidback on 2007-02-08
Have a look at this thread, Patrick had a mobo problem which he as resolved, maybe of interest.

[http://www.ubuntuforums.org/showthread.php?t=348016&page=3](http://www.ubuntuforums.org/showthread.php?t=348016&page=3)

---

