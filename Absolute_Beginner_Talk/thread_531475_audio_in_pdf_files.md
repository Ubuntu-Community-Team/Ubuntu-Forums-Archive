---
title: "audio in pdf files?"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Miroku on 2007-08-21
is there anyway that i can listen to audio that is embedded in pdf documents? under windows with acrobat, i can just click on links within each page but i dont get that option with kpdf. the audio files are in realplayer format which i have installed. has anyone figured how to do this? i dont like restarting so i can log back into windows just to hear the audio in that documentss.. please help.

TIA.

---

### Post by Hallvor on 2007-08-21
You probably need realplayer for that: 

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_RealPlayer_10_Multimedia_Player_.28RealPlayer.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_RealPlayer_10_Multimedia_Player_.28RealPlayer.29)

---

### Post by Miroku on 2007-08-21
realplayer is already installed

---

### Post by Paulmd on 2007-08-21
> **Miroku said:**
> is there anyway that i can listen to audio that is embedded in pdf documents? under windows with acrobat, i can just click on links within each page but i dont get that option with kpdf. the audio files are in realplayer format which i have installed. has anyone figured how to do this? i dont like restarting so i can log back into windows just to hear the audio in that documentss.. please help.

TIA.

You might need to get the genuine article Acrobat Reader instead of kpdf.

[www.debian-multimedia.org](www.debian-multimedia.org), which should be added to your /etc/apt/sources.list

as 

deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) stable main

then 

```
sudo apt-get update

sudo apt-get install acroread


```

---

### Post by Miroku on 2007-08-21
yes, i just tried that. apparently its missing some plugins that dont seem to exist. i dont know what else to do with it. guess i have to keep restarting. =(
thanks.

---

### Post by Paulmd on 2007-08-21
> **Miroku said:**
> yes, i just tried that. apparently its missing some plugins that dont seem to exist. i dont know what else to do with it. guess i have to keep restarting. =(
thanks.


The first time I tried to install Acrobat, I just went to Adobe's website and dumbly assumed that their inataller would actually work. It gave me much the same error. But you can click OK, and Acrobat will continue to load, and even open PDFs.

If you went thru the package manager at debian-multimedia.org, there are also some additional Acrobat plugins that you may need you your Audio. 

try 

```
sudo apt-get install acroread-plugins acroread-escript
```

and see if that helps any.

---

### Post by Miroku on 2007-08-22
i tried that. it does install a bunch of plugins. however, i believe i need the 'multimedia' plugin and thats not there. do you know of any way i can get that specific plugin? that is the plugin that is in my windows partition acrobat so i am thinking it is that. thanks.

---

### Post by Paulmd on 2007-08-23
> **Miroku said:**
> i tried that. it does install a bunch of plugins. however, i believe i need the 'multimedia' plugin and thats not there. do you know of any way i can get that specific plugin? that is the plugin that is in my windows partition acrobat so i am thinking it is that. thanks.


Hmmm.... Is the audio itself embedded in the PDF, or do the links just take you to an external website, which has the files?

Have you got realplayer to play audio within a browser window?  I've noticed that downloading and installing the .bin for realplayer doesn't really do a complete install. 

Also does Acrobat open up a regular PDF just fine? Here's a sample PDF to check with.

[http://docs.real.com/docs/flshccg.pdf](http://docs.real.com/docs/flshccg.pdf)

---

### Post by Miroku on 2007-08-24
the audio is embedded into the pdf (the size of the pdf is 192 MB). it does not open up any external programs/links whenever i use it in XP. 

my realplayer is fine also. it plays realaudio with no problem. i did have the browser integration plugin from mozilla but i am not sure if that makes any difference in this case.

---

