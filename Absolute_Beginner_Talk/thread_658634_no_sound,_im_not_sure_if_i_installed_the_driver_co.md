---
title: "no sound, im not sure if i installed the driver correctly"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by kellogs908 on 2008-01-04
I know there are similiar posts but nothing that I can find helps my particular problem.
The problem is pretty self explainitory, I have NO sound at all. I tried reinstalling the driver with what is provided at this link [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=24&Level=4&Conn=3&DownTypeID=3](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=24&Level=4&Conn=3&DownTypeID=3)
 I followed the steps that were provided in the readme, if someone wants to download it and take a look that would be very much appreciated, I cant figure out if i did soemthign wrong or if there are things I didn't do yet
basically i took the automatic install side of things, I will try the manual way but i get a bit confused exactly what to do at times

---

### Post by AKD on 2008-01-04
I seem to be having somewhat of the same problem as you. ( [http://ubuntuforums.org/showthread.php?t=658551](http://ubuntuforums.org/showthread.php?t=658551) ) I have no sound at all and it is also messing up anything that uses sound (flash, audio editors etc can't run at all and get the errors stated in the above thread thread).

---

### Post by kellogs908 on 2008-01-04
i have a quick question then. Does ubuntu automatically install most sound drivers or does it always have to be done manually?

---

### Post by AKD on 2008-01-04
I'm pretty sure that the sound drivers should be installed or will be installed when updated.

---

### Post by Tyke91 on 2008-01-04
ubuntu automatically installs sound drivers, but sometimes your sound card is either too new or too obscure (or just too evil) to be recognized by ubuntu. 

you should try to compile your alsa drivers from source. 

follow [this](https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28trouble%29%7C%28sound%29%7C%28shooting%29) link

---

### Post by kellogs908 on 2008-01-04
this may sound so very stupid of me to ask but what exactly does it mean by go to a shell

---

### Post by SidewinderPro2 on 2008-01-04
It may be pretty simple. I had to go through that Realtek HD trash myself. Onboard audio...

Try this out before you go to any extremes here. Click Applications, Accessories, and Terminal. A command prompt will open up (The DOS days come in handy)

Type this and then press enter:

```
alsamixer
```

Use your arrow keys to move side to side and press up to boost the sound. Chances are the sound has been muted. Max out all the colored bars, which maxes out the sound on all channels. Then press ESC (Escape key). Try playing something like a ripped CD track or some sort of audio file. Tell us how it goes from there. I can do screenshots if necessary.

---

### Post by Casual Fan on 2008-01-04
> **kellogs908 said:**
> this may sound so very stupid of me to ask but what exactly does it mean by go to a shell

Click on Applications>Accessories>Terminal

---

### Post by kellogs908 on 2008-01-04
basically the terminal is the shell?? if so this is waht i got for the first part
:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
#

Check to see if the ALSA driver for your sound card exists. Go to [WWW] [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main) and search for your sound card (chipset) manufacturer.

    *

      Success - You will have found the driver for your soundcard's chipset.
    *

      Failure - You will have not found the driver for your soundcard chipset. (at the moment I cannot help you, but stay tuned!)

i did this and i found toshiba which my computer is a toshiba but it has realtek audio and my computer isnt listed under audio

---

### Post by AKD on 2008-01-04
Maybe this might help with my problem. When I do what Sidewinder said I get this error:
```
alsamixer: function snd_ctl_open failed for default: No such device

```
Any ideas?

---

### Post by SidewinderPro2 on 2008-01-04
Hmm, you might not have the ALSA drivers installed or something. That may explain why it can't find it. Try this out, I ran through this among other things:

[http://www.alsa-project.org/main/index.php/Matrix:Main]("http://www.alsa-project.org/main/index.php/Matrix:Main")

Pick your model and follow the directions. In my case I selected Nvidia since its an onboard Nvidia chip. I followed the link, where I was presented with two options, one being the 430 nForce chipset. I clicked on that and followed the directions.

Its a pain in the neck trying to get sound working correctly in many operating systems if the drivers aren't easy to access for new guys. Linux just seems to be particularly difficult with soundcards. I went through multiple guides, installed a ton of crap and modified a few ALSA files. My sound works, its not as clear and rich as the sound I get from my Vista drive, but oh well. Been fighting for about a week for sound.

Check out my thread for more info, try some of the things Xeth listed. 

[http://ubuntuforums.org/showthread.php?t=652054]("http://ubuntuforums.org/showthread.php?t=652054")


Good luck with the sound. If Ubuntu could match the soundcard installation ease of XP it would be even cooler than it already is (Compiz Fusion had me sold)

---

### Post by kellogs908 on 2008-01-04
im not going to mess around too much with the manual install right now i have been messing around with it too much already today, thanks for the help there is some interesting ideas, your particular fix is one of the early fixes i tried and unfortunatly that wasnt the problem

---

### Post by bwtranch on 2008-01-04
Maybe you don't have the alsamixer installed. I didn't even know what it was. So, I cracked open a term and there it was Blam. Pretty cool.

---

### Post by kellogs908 on 2008-01-05
im pretty sure its installed i mean i can pull it up via the terminal/shell and it shows up under devices in the volume control

---

### Post by SidewinderPro2 on 2008-01-05
Have you tried editing the Alsa files yet? That may be the key to getting the sound working.

---

### Post by kellogs908 on 2008-01-05
im going to do a very basic recap of what i have and havnt done yet...
i went to the sound troubleshooting
tried step one, success the on board sound was installed
tried step two, success sound card was listed
next step search for your alsa driver on the site listed, i found it
next step type sudo modprobe snd-[NAME OF YOUR SOUNDCARD'S DRIVER, i did this and it worked but then it requested a password, i tried typing it in but it wont let me type in anything unless i type enter and then key it in really fast and even then it says the password is wrong

i have also tried typin in alsamixer into the shell to unmute it and that didnt appear to do anything although i could never tell if it was on mute in the first place

does all of this mean that my sound card is working and it is for sure something with the alsa driver thats wrong?

there is a section called using alpha source and it looks like a ton of work, it was also suggested changing the codecs, which i dont have a clue how to do

basically with what i have found out so far, what exactlly is that telling me? can we rule out certain things as the problem? and any other ideas on how to fix it would be appreciated

---

### Post by Yellow Pasque on 2008-01-05
Type in your password and hit enter as normal when prompted. The cursor is invisible as a security measure (you won't even see aterisks like you do when you type a lot of passwords).

If you get tired of playing with ALSA, you wouldn't be the first person. See my sig for an alternative sound system.

---

### Post by kellogs908 on 2008-01-05
actualy for me its blinking black and it literally wotn let my type anything unless I press enter first and then it says i typed in the wrong password
is that a bug or am i doing it wrong

---

### Post by Yellow Pasque on 2008-01-05
You're doing it wrong. Just type the password and hit enter. You won't get any visual feedback, but it's still "letting you type".

---

### Post by kellogs908 on 2008-01-05
srry bout that i figured out what you meant a bit before u posted it, but i decided to try to solution in ur sig anyways, it took five minutes and it really works, thanks a ton

---

### Post by Yellow Pasque on 2008-01-06
Awesome. If you ever run into problems with it, don't hesitate to post on the 4front forums or shoot me a PM.

---

