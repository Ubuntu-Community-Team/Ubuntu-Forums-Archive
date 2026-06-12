---
title: "Need help with installing fix for youtube"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Ribar on 2007-12-13
Hello guys,

I am new user to Linux, so hang with me hopefully i can explain myself. I am unable to play youtube videos in my firefox browser, even after i have updated the flash player. So what i am trying to do is find the repository for the youtube fix, and the key so i can download and install it. 

Could you guys give me a help with this? I am not sure where to begin, i have read through the starcraft's repository guide, and i am a little bit shaky as i am not sure where to look for repository's. Maybe i have this whole thing wrong.

-Ribar

---

### Post by Want A Pie on 2007-12-13
Im new too, and I also had that problem
up the top of your screen next to the time etc. there should be a little icon (grey or orange) that says that you have updates to download. Download them by clicking on it, then YouTube should work :D

---

### Post by Ribar on 2007-12-13
> **Want A Pie said:**
> Im new too, and I also had that problem
up the top of your screen next to the time etc. there should be a little icon (grey or orange) that says that you have updates to download. Download them by clicking on it, then YouTube should work :D

I did all the updates, but i still get the problem with youtube. When i try to play a video it asks me to search for a codec. I click yes, and then it finds it, and when i try to install it i get this error message. 

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by ubunter1 on 2007-12-13
im new as well,but have you installed the medibuntu repository [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by spiderbatdad on 2007-12-13
flashplayer-nonfree is the one i have. works perfectly

---

### Post by PmDematagoda on 2007-12-13
@Ribar:- Do as the error message suggested by doing:-

```
sudo dpkg --configure -a
```

That should fix your problem.

For the others, yes I use the flashplayer-nonfree as well and it works really well. If you want to install it on Firefox just simply visit a site with Flash content and the browser will give you the option of installing it. But this may not work if you already have a version of Flash installed.

---

### Post by Ribar on 2007-12-13
Ok i did execute the 

> sudo dpkg --configure -a

And that did install some files, but it did not fix the problem with youtube. When i go to youtube it just brings down my pc to slow speed it slows down everything until i close youtube. 

What do i need to do to remove what i just installed and do a fresh reinstall maybe some files did not install properly? Sorry for all these questions guys. :( I notice when i go to some websited that use flash the buttons don't display.

---

### Post by spiderbatdad on 2007-12-13
try running:```
sudo apt-get dist-upgrade && sudo apt-get update
```
then look in synaptic for flashplayer-nonfree. If it's installed, mark it for reinstallation.
Good luck.

---

### Post by papuccino1 on 2007-12-13
Here is the 100% WORKING fix for youtube on Firefox.

I just installed a fresh ground-zero Ubuntu and I installed it, everything works 100%.

Visit this site:

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Download the first option (.tar.gz)


After that finishes right click on the tar file and select "extract here". That's like unzipping in Windows.

Then open the folder and double click on the file "flashplayer-installer". Not the text one. And a pop-up should appear. Select "run in terminal" and then follow the instructions given. 

Pretty simple to follow.


REMEMBER TO CLOSE ANY AND ALL FIREFOX WINDOWS BEFORE INSTALLING THIS THING OR IT WON'T WORK. Let me know how it goes.

---

### Post by Ribar on 2007-12-13
> **papuccino1 said:**
> Here is the 100% WORKING fix for youtube on Firefox.

I just installed a fresh ground-zero Ubuntu and I installed it, everything works 100%.

Visit this site:

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Download the first option (.tar.gz)


After that finishes right click on the tar file and select "extract here". That's like unzipping in Windows.

Then open the folder and double click on the file "flashplayer-installer". Not the text one. And a pop-up should appear. Select "run in terminal" and then follow the instructions given. 

Pretty simple to follow.


REMEMBER TO CLOSE ANY AND ALL FIREFOX WINDOWS BEFORE INSTALLING THIS THING OR IT WON'T WORK. Let me know how it goes.

IT WORKED!!! hehe :)  You guys rock! :guitar:

Thanks for all the great help and advice, i still lot to learn. Now while i got the video working with you tube i realized that i don't have any sound, i guess its off to hunting down the sound drivers. :)

---

### Post by papuccino1 on 2007-12-13
Good to know it worked. :)

---

### Post by tothelandofnod on 2007-12-13
I just got YouTube working myself, thanks to all.

---

### Post by Ribar on 2007-12-14
> **tothelandofnod said:**
> I just got YouTube working myself, thanks to all.

Glad you were able to get it working too. :) I think it would be good idea to submit this somewhere where beginners could looked this fix up and implement it. I think it would help many people. Just an idea. :)

Btw. I found the fix to my sound card too. This will work for all the Chaintech AV710 sound cards. You have to go and copy the bellow text into a file called asound.conf and save it in you /etc folder.

> # copy this file in /etc/asound.conf (for all users) or $HOME/.asoundrc (just for you)
#
# this file map uses mixer as explained in
# [http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php](http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php)
# and explain what I discovered with trial and error
#
# I have Mandrake 9.2, Alsa 1.0.0.rc2, kernel 2.4.23,
# 6 channel amplifier connected to the card digital out (optical / red light)
# 2 channels connected to the analogic out
#
# run alsamixer from a terminal or konsol. Set everything to "PCM Out". 
# (but see below at KsCD)
#
# I have aRTs NOT enabled.
# If you want otherwise go to KDE Control Center, Sound Sytem, flag the field 
#       "Start aRTs soundserver on KDE startup".
# In the tab "Sound I/O" in the field 
#       " Use Custom Sound Device"
# insert /dev/sound/adsp to have output to the digital
# otherwise do not flag the field or use /dev/sound/dsp (without the 'a') 
# to use analog output
# use bottum "test" to test :)
#
# Also test sounds with KDE Control Center, LookNFeel, 
# System Notification, 
# Actions Play a Sound
# If you don't want to use aRTs but you do still want to have 
# KDE Sounds System Notification
# (I don't see any reason to do it) be sure to press "Player Settings..." 
# button and in the
# popup window use external player and type /usr/bin/aplay
# aRTs does not care about this configuration file
#
# in xmms 
#
#       press ctl+P, output plugin = Alsa 0.9, 
#       configure, user defined: default, 0, PCM.
#
# Output goes to Digital because of pcm.!default setting below.
# aRTs settings before explained do not affect xmms
#
# Totem Media Player: output goes to digital (because of pcm.!default setting below).
# aRTs setting before explained do not affect Totem
#
# my KsCD works if, within alsamixer, at least "IEC958" or "IEC958 1" is setted
# as "H/W in 0" or "H/W in 1". 
# You can even set both but in this case
# this setting (instead of "PCM out") void other digital sounds.
# aRTs setting before explained do not affect KsCD
# KsCD not care about this configuration file.
#
# mplayer (from terminal or konsole) works with: mplayer -ao alsa9:default avi1.avi
# if the option ao=alsa9:default is set in mplayer.conf it works 
# also with mplayer avi1.avi
# mplayer.conf is in /etc/mplayer/mplayer.conf (but read notes in the 
# files itself: there are other files as well)
#
# the gui version of mplayer (gmplayer) seeks the file /etc/mplayer/mplayer.conf 
# and then in your home .mplayer/config and then .mplayer/gui.conf.
# if the sound is not working verify ao option there.
# I did not understand everything here, but if you delete gui.conf 
# the file is recreated
# by gmplayer. In my experience it creates also an entry ao_driver = "alsa9" that must
# be corrected as ao_driver = "alsa9:default"
# if you launch via command line you can use gmplayer -ao alsa9:default avi1.avi
# or use MenuDrake to add the -ao option to the menu command.
# Running from a terminal or konsole I have several warning messages like:
# alsa-control: mixer attach default error: Invalid argumentA:   5,5 V:   5,5 A-V:
# or
# alsa-control: unable to find simple control 'PCM',0 3%  4%  0,9% 3 0 92%
# but the system seems to work fine
#
# A note about mixers.
# Mixer allow you to share the sound device between different applications 
# and have different
# sounds mixed toghether. aRTs is a mixer. This configuration file provide a 
# mixer as well.
# I don't have problems not using aRTs.
#
# Take care
# Alessandro Vallega

pcm.!default {
        type plug
        slave.pcm "dmixer"
}

pcm.dmixer  {
        type dmix
        ipc_key 1024
        slave {
                pcm "hw:0,1"
                format S32_LE
                period_time 0
                period_size 1024

# increased buffer_size because in my system 1024 cause bad
# audio performance (for totem media player and mplayer)
                buffer_size 8096

                rate 44100
        }
        bindings {
                0 0
                1 1
        }
}

ctl.dmixer {
        type hw
        card 0
        device 1
}

#

In case anyone needs it, and has the same sound card, this will work for you. :)

---

