---
title: "Synaptic vs Add Software"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by paker on 2007-02-12
I am still new to Ubuntu. Here are a few questions I have:

1) I know I can get new programs from Synaptic. What about Applications>Add Software? Are they different?

2) After installing Ubuntu 6.10 32-bit, I installed EasyUbuntu. It added nvidia driver among others, but I still had to do "sudo xconfig-nvidia." What does this line do? Does Synaptic do this line automatically?

3) From Add Software I marked Wine Windows Emulator and installed it. How do I actually use it? I need to view .nwc format documents (music scores) and they don't have a linux driver. I am not asking step by step process. I ask someone to explain to me the principle of running Wine in Dummy language (which is my language).

4) I need to rip CD's to mp3. Is ripping not built in SoundJuicer?

5) I like Ubuntu so far. 99% of the programs I need get installed in one big step. What I am finding overwhelming is that I have to add features one by one. Is there an article or thread that someone prepared for newbies like me? 

Many thanks.

---

### Post by Maestro23 on 2007-02-12
For your #3: [http://www.winehq.com/site/docs/wineusr-guide/index](http://www.winehq.com/site/docs/wineusr-guide/index)

---

### Post by igknighted on 2007-02-12
> **paker said:**
> I am still new to Ubuntu. Here are a few questions I have:

1) I know I can get new programs from Synaptic. What about Applications>Add Software? Are they different?

2) After installing Ubuntu 6.10 32-bit, I installed EasyUbuntu. It added nvidia driver among others, but I still had to do "sudo xconfig-nvidia." What does this line do? Does Synaptic do this line automatically?

3) From Add Software I marked Wine Windows Emulator and installed it. How do I actually use it? I need to view .nwc format documents (music scores) and they don't have a linux driver. I am not asking step by step process. I ask someone to explain to me the principle of running Wine in Dummy language (which is my language).

4) I need to rip CD's to mp3. Is ripping not built in SoundJuicer?

5) I like Ubuntu so far. 99% of the programs I need get installed in one big step. What I am finding overwhelming is that I have to add features one by one. Is there an article or thread that someone prepared for newbies like me? 

Many thanks.

1) Synaptic and Add/Remove software install from the same repositories, but the interface is different.  I also feel like more packages are available in Synaptic.

2) The easy-ubuntu program installs the driver, but the xconfig-nvidia command tells your system that is the driver to use (instead of the one it currently is using).

3) Check out [www.winehq.com](www.winehq.com) for instructions, I don't use wine so I couldn't tell you.  For music scores, have you tried finding a linux program?  There are a few good ones.

4) SoundJuicer's primary task is ripping music.  I would steer you away from mp3, as .ogg is a much better format.  Some mp3 players can't use ogg however, so check if yours does.  To get mp3 support you need to install all available codecs if you havent already.  One final thought, if you have tried all these things and no success, search the forums here as there is bound to have been someone with this issue, so the solution is probably here somewhere.

5) Try [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/).  There are a ton of tutorials here that explain how to do things.

---

### Post by konst88 on 2007-02-12
[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by Luk0r on 2007-02-12
> **paker said:**
> 3) From Add Software I marked Wine Windows Emulator and installed it. How do I actually use it? I need to view .nwc format documents (music scores) and they don't have a linux driver. I am not asking step by step process. I ask someone to explain to me the principle of running Wine in Dummy language (which is my language).

Simply put, Wine allows you to run some Windows applications in Linux.  If you want the latest and greatest version of Wine, I suggest you add the Wine APT repo by following [this guide]("http://www.winehq.org/site/download-deb").

If you want to try and run a Windows app in Linux, install wine, open up a terminal and do:
```
cd <the directory the app's installer is>
wine <the installer exe file>
```

---

### Post by Unisted on 2007-02-12
Regarding point 4, installing items via Synaptic generally is quite easy as it marks all the required packages for you.

In addition when you consider what you have to do to get a copy of Windows XP up and running and the packages your required to install it's really not that bad.

Off hand I can think that on Windows I would need to install SP2 and all the updates, anti virus, spyware, nero, winzip, itunes, MS Office, divx and all associated codecs, firefox, thunderbird etc... etc...

If your hardware is supported out of the box by Ubuntu then your flying within one or two hours.

---

### Post by Nythain on 2007-02-12
> **paker said:**
> I am still new to Ubuntu. Here are a few questions I have:

1) I know I can get new programs from Synaptic. What about Applications>Add Software? Are they different?

2) After installing Ubuntu 6.10 32-bit, I installed EasyUbuntu. It added nvidia driver among others, but I still had to do "sudo xconfig-nvidia." What does this line do? Does Synaptic do this line automatically?

3) From Add Software I marked Wine Windows Emulator and installed it. How do I actually use it? I need to view .nwc format documents (music scores) and they don't have a linux driver. I am not asking step by step process. I ask someone to explain to me the principle of running Wine in Dummy language (which is my language).

4) I need to rip CD's to mp3. Is ripping not built in SoundJuicer?

5) I like Ubuntu so far. 99% of the programs I need get installed in one big step. What I am finding overwhelming is that I have to add features one by one. Is there an article or thread that someone prepared for newbies like me? 

Many thanks.

I know most of this has already been answered but ill throw my two cents in

1. Synaptic shows every possible package available in the repos you have specified in your /etc/apt/sources.list while add/remove software just lists software packages... so i would recoment synaptic, though if/once you are comfortable with the CLI then familiarize yourself with aptitude

2. Was already answered, though i have never had success with easyubuntu, automatix, or the nvidia driver in repo... though i have to reinstall drivers everytime i update kernel (almost never) i manually install the drivers via the pkg.run file from nvidia's site

3. to run just about anything in wine, if you are in the directory containing the exe then its just wine your.exe also i believe but im not sure wine path/to/your.exe would work to, thats for installers and then running the apps after they are installed

4. not sure cause i havent ripped a cd since using linux

5. automatix takes care of a lot of default stuff, similar to easyubuntu, then there's the ubuntu guide at [http://ubuntuguide.org](http://ubuntuguide.org)

and there we have it, as far as i know that should all be pretty accurate and to the point

---

### Post by teaker1s on 2007-02-12
if you set mark recommended as dependencies:KS

---

### Post by paker on 2007-02-12
Many thanks for kindly answering my questions.

---

### Post by dcstar on 2007-02-13
> **paker said:**
> I am still new to Ubuntu. Here are a few questions I have:

.....
4) I need to rip CD's to mp3. Is ripping not built in SoundJuicer?
.....
Many thanks.

I have **grip** set up to rip my CDs on insert and automatically create MP3's, there is a good Howto in the forum.

---

### Post by tonyr1988 on 2007-02-13
As to #4, I would personally recommend installing Goobox (it's in Synaptic under goobox). I found it extremely easy for ripping MP3s. It will show up in the Sound & Video menu under a generic name - I don't remember what it is exactly, but it won't be under "Goobox," it'll be something like "CD Ripper"

---

