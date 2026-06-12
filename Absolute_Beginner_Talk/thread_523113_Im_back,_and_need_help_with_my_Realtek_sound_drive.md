---
title: "Im back, and need help with my Realtek sound drivers"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by jake16424 on 2007-08-11
please help, just let me know what you need to help me , and ill get all the information you need from my pc,, 

right now im running windows XP but i can switch it to ubuntu in a instant by rebooting,, so im me or reply to this post,, i hope you guy's can help =) the best


Jake

---

### Post by RomeReactor on 2007-08-11
Hi again. If you switch to Ubuntu, what's the output of this command?
```
sudo lshw -class multimedia
```

---

### Post by jake16424 on 2007-08-11
> **RomeReactor said:**
> Hi again. If you switch to Ubuntu, what's the output of this command?
```
sudo lshw -class multimedia
```

allright,, ill go right back to it. =)

---

### Post by jake16424 on 2007-08-11
hey, that's a pretty nifty command, =)

 *-multimedia
       description: Multimedia audio controller
       product: nForce3 250Gb AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@00:06.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: driver=Intel ICH
       resources: ioport:ac00-acff ioport:b000-b07f iomemory:db001000-db001fff irq:193



there you go, =)

---

### Post by RomeReactor on 2007-08-11
What's the output of:
```
aplay -l
```
(sorry for not asking earlier).

Go into "System->Preferences->Sound" and where it says **Default Mixer Tracks** make sure the Device is set to **Intel ICH**. Do you have any audio or video files to play on your Ubuntu system? if so, start playing one so we know if and when the sound starts working. Or if your internet is working fine there, open Rhythmbox, select "Radio" on the left and start playing an internet radio station.

> **jake16424 said:**
> hey, that's a pretty nifty command, =)
Yeah, it's very useful. Run it as **sudo lshw** and it will list all your hardware! :)

---

### Post by jake16424 on 2007-08-11
> **RomeReactor said:**
> What's the output of:
```
aplay -l
```
(sorry for not asking earlier).

Go into "System->Preferences->Sound" and where it says **Default Mixer Tracks** make sure the Device is set to **Intel ICH**. Do you have any audio or video files to play on your Ubuntu system? if so, start playing one so we know if and when the sound starts working. Or if your internet is working fine there, open Rhythmbox, select "Radio" on the left and start playing an internet radio station.


Yeah, it's very useful. Run it as **sudo lshw** and it will list all your hardware! :)

-------------------------------------------------------------------------------------------------------------------------------------
here it is 

jacob@jacob-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK8S [NVidia CK8S], device 0: Intel ICH [NVidia CK8S]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK8S [NVidia CK8S], device 2: Intel ICH - IEC958 [NVidia CK8S - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jacob@jacob-desktop:~$



and for the record,, it was on the intel one from default,, so,, yeah, i downloaded music files VIA: limewire 4.12 and, didnt get a fart of sound..:(

---

### Post by RomeReactor on 2007-08-11
If you now have a file playing, from the terminal enter:
```
alsamixer
```
on the very first item there (IEC958 ) press **m** to mute/unmute it. Anything?

---

### Post by jake16424 on 2007-08-11
> **RomeReactor said:**
> If you now have a file playing, from the terminal enter:
```
alsamixer
```
on the very first item there (IEC958 ) press **m** to mute/unmute it. Anything?


jacob@jacob-desktop:~$ alsamixer
No mixer elems found

jacob@jacob-desktop:~$



yeah,, we got an equivilent of an error, =(...:(

ah,, i dont even have my audio drivers installed,, i can't get them to install,, so,, yeah just so you know.. ^_^

---

### Post by RomeReactor on 2007-08-11
Where did you get the drivers from?

---

### Post by jake16424 on 2007-08-11
> **RomeReactor said:**
> Where did you get the drivers from?

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=23&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false#AC]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=23&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false#AC")

---

### Post by RomeReactor on 2007-08-11
Which of the four Linux drivers was it?

---

### Post by jake16424 on 2007-08-11
Linux(kernel version 2.2.14 or 2.4)

---

### Post by RomeReactor on 2007-08-11
OK, I'm downloading them; let me check...

---

### Post by RomeReactor on 2007-08-11
The file extracted as a folder named **realtek-linux-audiopack-3.5-6**; do you still have it? If so, move it to your home folder, and from the terminal:
```
 cd realtek-linux-audiopack-3.5-6
```
and
```
sudo ./install
```

---

### Post by jake16424 on 2007-08-11
whheeeee, =D

---

### Post by jake16424 on 2007-08-11
yep, still not working =(

---

### Post by jake16424 on 2007-08-11
> **RomeReactor said:**
> The file extracted as a folder named **realtek-linux-audiopack-3.5-6**; do you still have it? If so, move it to your home folder, and from the terminal:
```
 cd realtek-linux-audiopack-3.5-6
```
and
```
sudo ./install
```

like previously stated im a newb, where is the "HOME" folder? O_o

---

### Post by jake16424 on 2007-08-11
> **RomeReactor said:**
> The file extracted as a folder named **realtek-linux-audiopack-3.5-6**; do you still have it? If so, move it to your home folder, and from the terminal:
```
 cd realtek-linux-audiopack-3.5-6
```
and
```
sudo ./install
```

ok well i found it.

and i put the archived downloaded driver file thingy in there,, copy pasted what you said todo, and this is what i got.

jacob@jacob-desktop:~$ cd realtek-linux-audiopack-3.5-6
bash: cd: realtek-linux-audiopack-3.5-6: No such file or directory
jacob@jacob-desktop:~$

---

### Post by RomeReactor on 2007-08-11
It's the one that opens when you click on "Places->Home Folder". If you have that folder on your desktop, the the commands would be:
```
cd Desktop/realtek-linux-audiopack-3.5-6
```
and
```
sudo ./install
```
I have to go. I'll be back later.

---

### Post by jake16424 on 2007-08-11
> **RomeReactor said:**
> It's the one that opens when you click on "Places->Home Folder". If you have that folder on your desktop, the the commands would be:
```
cd Desktop/realtek-linux-audiopack-3.5-6
```
and
```
sudo ./install
```
I have to go. I'll be back later.

i get the same message,, i put it in the home folder,, and i got that damned file could not be found or directory incorrect or whatever,,, >=(

---

### Post by RomeReactor on 2007-08-11
Remember to extract it first. What you have to put in your home folder is the **extracted folder** from the .tar.bz2 file you downloaded. If you put the compressed file in your home folder, just double-click on it and select "extract".

---

