---
title: "Help!!!!"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by Ganda_Melga on 2007-04-09
Hi, I have just installed Xubuntu. It looks very nice, but I have this huge problem. I have no sound whatsoever. What do I do??? In windows ME the card was recognised. It's an old soudblaster, it fits into the old big brown slots.

I have always used windows, and I must say I'm quite lost in linux. Theres is no windows explorer, no device manager so I can't see what installed or not.

Anybody can help me? Please?

---

### Post by bodhi.zazen on 2007-04-09
What ? What ? No sound you say ?

Hard to know what to advise. It could be a number of problems. Was sound working with the live CD?

First I assume you also have an on-board sound card ? Right click on your sound mixer (the lilltl speaker) and try changing devices.

Second, not to ask the obvious, but make sure the sound is not muted.

From there, what type of sound card ? What are you trying to listen to ?

See here for more information :

[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by terdon on 2007-04-09
Ubuntu has a "device manager" under system=>administration

How are you checking for sound?

PS. In general, try using a more informative subject. That way more people will read your post.

---

### Post by Ganda_Melga on 2007-04-09
> **bodhi.zazen said:**
> What ? What ? No sound you say ?

Hard to know what to advise. It could be a number of problems. Was sound working with the live CD?

First I assume you also have an on-board sound card ? Right click on your sound mixer (the lilltl speaker) and try changing devices.

Second, not to ask the obvious, but make sure the sound is not muted.

From there, what type of sound card ? What are you trying to listen to ?

See here for more information :

[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)



Hum....It's not an onboard card. Nor does the board have an onboard card. It's an old card from Soundblaster (Soundblaster AWE, or something like that).

The sound mixer doesn't show any device at all.


No, the sound is not muted.

I tried to listen a Cd with WAV tracks, MP3 tracks, Mpg movie clips. The image on the clip works fine, but no sound.

The application on xubuntu is the defauls one - Gxine.

Also while browsing the foruns I came across this instruction:

sudo modprobe snd-als100

I typed it in the terminal and the answer was:

FATAL: Error inserting snd_als100 (/lib/modules/2.6.17-10-generic/kernel/sound/isa/snd-als100.ko): No such device

Any help you can give me?


Sorry, about the typing errors, I'm from Portugal and my English is quite rusty.

---

### Post by Ganda_Melga on 2007-04-09
> **terdon said:**
> Ubuntu has a "device manager" under system=>administration

How are you checking for sound?

PS. In general, try using a more informative subject. That way more people will read your post.


Err.... I can't see that menu.... I have xubuntu, are the menus the same?


Applications - Settings - Mixer settings   (I used this menu) and also:

Applications - Settings - Settings manager

---

### Post by arvevans on 2007-04-09
If running Ubuntu "Edgy", then **System/Administration/Device Manager** will tell you what the system thinks your sound  card is, or if it even sees it.

Then **System/Preferences/Sound** will help test and configure your sound devices.

Arv
_._

---

### Post by bodhi.zazen on 2007-04-09
Try this :

In a terminal type :

```
sudo modprobe snd-sbawe
```

Log out of XFCE and back in

Re-try your sound card ...

---

### Post by Sef on 2007-04-09
I have had the same problem; here's how I got my sound working.

Open the terminal and type this:

gksudo mousepad /etc/modprobe.d/alsa-base

I needed to comment out a line (i.e. stop a piece of code (software) from working.)

This is the [thread]("http://ubuntuforums.org/showthread.php?t=160576&highlight=sound") where I received the help.

---

### Post by arvevans on 2007-04-09
OK.  XUbuntu uses different menus, as does KUbuntu.  Someone with XUbuntu will probably be more able to help you.  I have run XUbuntu, but it is not the one on my computer at present.
Arv
_._

---

### Post by annda on 2007-04-09
xubuntu uses xfce as window manager, not gnome like ubuntu, so your menus are different. unless someone using xfce comes along, you will have to manage with command line to solve the problem.

that said, you have an old ISA card. i found some useful suggestions here (look for ISA):
[https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)

where did you get the suggestion about "modprobe snd-als100"? if you still have the link to that thread, you could post it here, so we might take a look...

---

### Post by Ganda_Melga on 2007-04-09
> **bodhi.zazen said:**
> Try this :

In a terminal type :

```
sudo modprobe snd-sbawe
```

Log out of XFCE and back in

Re-try your sound card ...


Great! Now I already have sistem sounds. Although a bit scratchy....
But I still can't play any music files from the CD. What did I do wrong??

---

### Post by bodhi.zazen on 2007-04-09
> **Ganda_Melga said:**
> Great! Now I already have sistem sounds. Although a bit scratchy....
But I still can't play any music files from the CD. What did I do wrong??

OK, lets set-up your system so the driver loads on boot.

Open a terminal.

Type in : ```
sudo nano /etc/rc.local
```

Add this line ABOVE the line "exit 0" :> modprobe snd-sbawe

You do not need the "sudo" since /etc/rc.local is run at boot as root ...

OK, save to save the canges type Control-X, then type Y to save changes.

In terms of poor sound quality, I am not sure. That is the driver listed for your card, and more then that I do not know.

In terms of playing your CD, you need to install a few of those restricted formats.

Take a look at this link ...  [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

If the restricted formats are installed, what application are you using to play music (I am not too familiar with the default applications on xubuntu) ?

---

### Post by Ganda_Melga on 2007-04-09
> **annda said:**
> xubuntu uses xfce as window manager, not gnome like ubuntu, so your menus are different. unless someone using xfce comes along, you will have to manage with command line to solve the problem.

that said, you have an old ISA card. i found some useful suggestions here (look for ISA):
[https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)

where did you get the suggestion about "modprobe snd-als100"? if you still have the link to that thread, you could post it here, so we might take a look...



I got it here:

[https://answers.launchpad.net/ubuntu/+source/evince/+ticket/2323](https://answers.launchpad.net/ubuntu/+source/evince/+ticket/2323)

Was it incorrect of me to search other spots? It's listed in the Xubuntu site ([www.xubuntu.com](www.xubuntu.com))

---

### Post by Ganda_Melga on 2007-04-09
> **bodhi.zazen said:**
> OK, lets set-up your system so the driver loads on boot.

Open a terminal.

Type in : ```
sudo nano /etc/rc.local
```

Add this line ABOVE the line "exit 0" :

You do not need the "sudo" since /etc/rc.local is run at boot as root ...

OK, save to save the canges type Control-X, then type Y to save changes.

In terms of poor sound quality, I am not sure. That is the driver listed for your card, and more then that I do not know.

In terms of playing your CD, you need to install a few of those restricted formats.

Take a look at this link ...  [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

If the restricted formats are installed, what application are you using to play music (I am not too familiar with the default applications on xubuntu) ?


Ok... I typed the following line, as instructed:

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui


The terminal replied:

A Ler Listas de Pacotes... Pronto
Construindo Árvore de Dependências       
Reading state information... Pronto 
E: Impossível encontrar o pacote gstreamer0.10-pitfdll

Wich translated should read something like this:

reading packages list  -  ready
Building (.......) tree
Reading state information - ready
E: impossible to find the package gstreamer0.10-pitfdll


What do I try next?

---

### Post by bodhi.zazen on 2007-04-09
Again, not to ask the obvious, but did you enable your repositories ?

If not, enable away and re-try

If so, copy and paste that command (highlight the text with the mouse, move to the terminal, at the command prompt push the middle button (mouse wheel) down.

If you get the same error, remove the reference to the package. Like this :

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

---

### Post by Ganda_Melga on 2007-04-09
> **bodhi.zazen said:**
> Again, not to ask the obvious, but did you enable your repositories ?

If not, enable away and re-try

If so, copy and paste that command (highlight the text with the mouse, move to the terminal, at the command prompt push the middle button (mouse wheel) down.

If you get the same error, remove the reference to the package. Like this :

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui



Errrrr.....what is a repositorie? :confused: :confused:

---

### Post by bodhi.zazen on 2007-04-09
LOL I thought so !

[https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096)

---

### Post by Ganda_Melga on 2007-04-09
> **bodhi.zazen said:**
> LOL I thought so !

[https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096)


I'll check this link tomorrow. Anyway, I've messed around with the sistem, found some sort of updater of some kind, and now at least the MP3 already play. I'll check the others tomorrow, because here im Portugal is 1:30 AM, and i've got to catch some shut eye.l At 7 am it's time to go for work. :) 

Many thanks for your kind help. Also the other members were very helpfull, and I've learned a bit about linux with you and their help.

Thanks a lot!!


(tomorrow probably I'll be back with more doubts...:)

---

