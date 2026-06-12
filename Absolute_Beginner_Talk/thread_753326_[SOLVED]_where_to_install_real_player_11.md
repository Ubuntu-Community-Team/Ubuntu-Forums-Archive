---
title: "[SOLVED] where to install real player 11?"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by bhadotia on 2008-04-12
I've downloaded a .bin file for installing. It is asking me where to put it; what should i enter?

---

### Post by djbsteart1 on 2008-04-12
If you right click the file then under permissions select "executable" then double click the file, it should install automatically. If not, install it in 

/usr/bin

Donald

---

### Post by bhadotia on 2008-04-12
Alright the player has installed ; but there is  now folder RealPlayer on my desktop: can delete it or move it somewhere else?

---

### Post by djbsteart1 on 2008-04-12
was the folder there before installation or not, if it wasn't I don't think you can as it will contain the program files.

---

### Post by Shii on 2008-04-12
I just tried it myself. The RealPlayer folder contains the program. If you want to "install" it you have to go the terminal and run the installer with sudo.

---

### Post by bhadotia on 2008-04-13
just moved the folder  with proper arrangements( if you want i can detail them ) and realplayer is working  fine .

---

### Post by ptr0 on 2008-04-13
You don't have problems with ALSA? I'm asking because player works fine with OSS, with default ALSA settings audio is not working, the settings are:
> 
PCM device: default
5.1 PCM device: plug:surround51

I looked up audio settings in skype, and they're not default, but:
> HDA ATI SB (hw:SB,0)
I have card HDA ATI SB, Realtek ALC883. If I write in RealPlayer Hardware settings:
> PCM device: hw I can hear some sound, but it's too fast (and there are breaks while playing).  
I wonder, what should I write in "5.1 PCM device" field to make it work?

---

### Post by bhadotia on 2008-04-13
Actually I also noticed that I am having the same problem with both ALSA and OSS.

What I meant by player working fine is that atleast the player is launching from the menu- last time I had problem even in launching it when I movwd the file .

Actually realplayer performance is pathetic; download win32 codecs if you want to play real media . I installed the player because some rare real media audio was not playing correctly now atleast I can hear something understandable with realplayer.

If you want to know how to install win32 look [here]("http://tuxenclave.wordpress.com/2008/01/03/how-to-enable-multimedia-suport-in-ubuntu-710/")

---

### Post by Mach1US on 2008-04-18
To properly install RealPlayer download the real player from [www.real.com](www.real.com) , go to terminal, in terminal "cd" to the place where you have downloaded your Player ( usually /home/_YourName_/Desktop ) and execute the following :
[PHP] sudo dpkg -P realplay
 sudo aptitude install helix-player mozilla-helix-player[/PHP]
hope this helps

---

### Post by bhadotia on 2008-04-18
Ok.. thanks!

---

### Post by Mach1US on 2008-04-18
Some other reeds if you have any other problems:

[http://ubuntuforums.org/showthread.php?t=661833&highlight=realplayer+install](http://ubuntuforums.org/showthread.php?t=661833&highlight=realplayer+install)
[http://tuxenclave.wordpress.com/2008/01/03/how-to-enable-multimedia-suport-in-ubuntu-710/](http://tuxenclave.wordpress.com/2008/01/03/how-to-enable-multimedia-suport-in-ubuntu-710/)
[http://mplayerplug-in.sourceforge.net/config.php](http://mplayerplug-in.sourceforge.net/config.php)

---

### Post by bhadotia on 2008-04-19
Thank you very much.

---

