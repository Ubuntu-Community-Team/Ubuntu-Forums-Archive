---
title: "your video solution"
date: 2005-07-27
forum: Absolute Beginner Talk
---

### Post by MarcN on 2005-07-27
can someone tell me a real good movie player? 
i still have problems handling all the formats, and i tried a lot of players ,
got an .wmv file here and can't open it with anything ;(

tried caffeine , mplayer ,xine ,xmms and vlc , nothing works ;(

---

### Post by sonny on 2005-07-27
For me I think Mplayer is quite good for video, and for audio I recomend amarok, but I think your problem is about the video codecs wich you have to install, you can check the Ubuntu Guide here to install the multimedia codecs: [http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

---

### Post by MarcN on 2005-07-27
[QUOTE=sonny]For me I think Mplayer is quite good for video, and for audio I recomend amarok, but I think your problem is about the video codecs wich you have to install, you can check the Ubuntu Guide here to install the multimedia codecs: [http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)[/QUOTE]
 thx  , installed those plugins, but i cant download sudo apt-get install gstreamer0.8-lame, when doing it in the konsole it tells me :


Die folgenden Pakete haben nichterfüllte Abhängigkeiten:
  gstreamer0.8-lame: Hängt ab: libc6 (>= 2.3.2.ds1-21) aber 2.3.2.ds1-20ubuntu13 soll installiert werden


i use amarok for sound too, but also there is a problem, it always crashes when the playlist is done :(

---

### Post by majikstreet on 2005-07-27
[QUOTE=MarcN]thx  , installed those plugins, but i cant download sudo apt-get install gstreamer0.8-lame, when doing it in the konsole it tells me :


Die folgenden Pakete haben nichterfüllte Abhängigkeiten:
  gstreamer0.8-lame: Hängt ab: libc6 (>= 2.3.2.ds1-21) aber 2.3.2.ds1-20ubuntu13 soll installiert werden


i use amarok for sound too, but also there is a problem, it always crashes when the playlist is done :([/QUOTE]
 It might help if you translate that to english because you are in the english forum.

I translated it at Babel Fish for you (let me know if it's incorrect):
The following packages have not-fulfilled dependence: gstreamer0.8-lame: Depends: libc6 (= 2.3.2.ds1-21) however 2.3.2.ds1-20ubuntu13 is to be installed

---

### Post by poofyhairguy on 2005-07-27
[QUOTE=MarcN]can someone tell me a real good movie player? 
i still have problems handling all the formats, and i tried a lot of players ,
got an .wmv file here and can't open it with anything ;(

tried caffeine , mplayer ,xine ,xmms and vlc , nothing works ;([/QUOTE]

Gxine. for me, nothing beats gxine. I say "if Gxine can't do it, no Linux media player can."

---

### Post by sonny on 2005-07-27
[QUOTE=majikstreet]It might help if you translate that to english because you are in the english forum.

I translated it at Babel Fish for you (let me know if it's incorrect):
The following packages have not-fulfilled dependence: gstreamer0.8-lame: Depends: libc6 (= 2.3.2.ds1-21) however 2.3.2.ds1-20ubuntu13 is to be installed[/QUOTE]
If you are using synaptics you can select the package (libc6), then go to the package menu, and click on force version. I think that should help.

---

### Post by bored2k on 2005-07-27
VLC as main. Totem-Xine for others VLC can't.

---

### Post by MarcN on 2005-07-27
it's translated very well, and as i can play another .wmv file without problems, i guess that the other file is damaged, so thanks for the hint with the codecs ;)

---

