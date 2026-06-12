---
title: "Sound Issue!"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by B34ST1Y on 2007-12-12
Ok, so I just *re*-installed gutsy ubuntu for the 4th time, trying to get this stupid audio working. Upon a clean install, it appears to read my card and the computer doesn't give any errors when I try to play a sound file (ie, an .mp3), it even shows in the media player that it's playing....but no matter WHAT i do...I can't get any sound out. :(    what's the deal? Noob mistake?

---

### Post by meborc on 2007-12-12
open alsamixer from terminal```
alsamixer
```now move with your right arrow and unmute all channels (key M)... see if maybe there is a channel muted that you should use

EDIT: to play mp3's you need to install proper codecs ```
sudo apt-get install ubuntu-restricted-extras
```
there are some legal issues in using mp3 codecs in US and some other countries

---

### Post by B34ST1Y on 2007-12-12
it doesn't look like any of them are muted....but there's one called PCM, that I can't toggle mute or unmute it doesn't have 00's under it

---

### Post by meborc on 2007-12-12
thats strange, my soundcard is a bad one, so it actually plays sound from the PCM channel :)

are you sure you have all codecs installed as i posted?

---

### Post by B34ST1Y on 2007-12-12
lol way to go and all sneaky like, edit it on me :-P



when I try that code I get this:

b34st1y@zer0cool:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for b34st1y:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras

---

### Post by meborc on 2007-12-12
ok... you need to enable the extra repositories... you can do that by editing your /etc/apt/sources.list file```
gksudo gedit /etc/apt/sources.list
```now you need to remove the # from the lines that start with **deb** and ONLY from them... there should be max 4 lines that are still commented out, after that do```
sudo apt-get update
```and then try to install again ;)

---

### Post by B34ST1Y on 2007-12-12
mmmh, nvm I added a repository in synaptics package manager...and I found the package. update*****installing***

---

### Post by meborc on 2007-12-12
> **B34ST1Y said:**
> mmmh, nvm I added a repository in synaptics package manager...and I found the package. update*****installing***

:) it is much easier to try to help with giving the terminal command than to try to explain which menu to use and which tab to click on

sorry

---

### Post by B34ST1Y on 2007-12-12
well....now it thinks that it can play mp3's as I get it's visualize feed. :( still no sound. -_- if it helps I have an Everex XT5000T laptop, and the soundcard is a Realtek ALC885 High-Definition Audio

---

### Post by meborc on 2007-12-12
well, this could of have saved us some time... did a quick search with your soundcard... check this [http://ubuntuforums.org/showthread.php?t=636550&highlight=Realtek+ALC885](http://ubuntuforums.org/showthread.php?t=636550&highlight=Realtek+ALC885)

not sure what the result there is though... reading as i type

EDIT: ok... there is no feedback if the dude with the same card got it working with this script... but since he is not back to bash, you should give it a try ;)

---

### Post by B34ST1Y on 2007-12-12
ok, so upon following that link, I get linked to this page:

[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)


and it tells me to run some permission modifier script (take a look at it) but idk where the default alsa install thingie is ??

---

### Post by meborc on 2007-12-12
click on "here" in the sentence which starts like "Download..."

and save this file to your home folder

now open nautilus, brows to the file... right click and properties... and check the boxes to make it executable

now fire up the terminal and type```
sudo ./alsa_setup.sh
```

EDIT:

you can do **chmod 755 ~/alsa_setup.sh** in stead of the nautilus-right-click-permissions way

sorry if i am unclear :)

---

### Post by thelatinist on 2007-12-12
I took a look at the script, and it should be safe to run it as sudo.  It will install files from sources I am not familiar with, so I can't vouch for the files themselves.

---

### Post by B34ST1Y on 2007-12-12
Thanks for the help guys, somehow I only get sound if I have my headphones plugged in.....but the internal speakers dont work. Any Ideas?

---

