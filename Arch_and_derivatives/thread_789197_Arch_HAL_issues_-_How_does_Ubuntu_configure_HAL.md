---
title: "Arch HAL issues - How does Ubuntu configure HAL?"
date: 2008-05-10
forum: Arch and derivatives
---

### Post by Farghal on 2008-05-10
Hello everybody. I converted from Ubuntu to Arch, and I'm lovin' it :-)

But, I have some problems regarding my generic USB mp3 player:
1) I want HAL to mount the player with UTF-8 encoding like it did in Ubuntu. Right now, it shows Arabic characters as ??????.

2) In Ubuntu, it used to recognize the player as an MP3 player, give it a nice icon, and add it as a music source in Rhythmbox. In Arch, on the other hand, the player is mounted as a generic USB flash drive. How can I make Arch recognize it as an MP3 player?

I asked on the Arch bbs and [I was advised]("http://bbs.archlinux.org/viewtopic.php?pid=366206#p366206") to check how Ubuntu configures HAL. I don't have Ubuntu here anymore and even if I did, I don't think I'd know where to look. Help.

Thanks in advance.

---

### Post by hyperair on 2008-05-10
My thumbdrive and phone display chinese characters just fine on Arch. Why don't you check your /etc/rc.conf to see if your locale is with encoding utf-8?

---

### Post by Farghal on 2008-05-10
Thanks for the speedy response, hyperair.

My locale is ar_EG.utf8. So why is HAL not mounting with utf8?

---

### Post by hyperair on 2008-05-10
Heh now I'm stumped. What DE are you using, if any?

---

### Post by Farghal on 2008-05-10
I'm using Gnome. And earlier in this same installation I had installed XFCE and thunar couldn't read the Arabic filenames on the player either.

This is the first encoding problem I come across in like 3 years of linux. That's why I think the problem is that I didn't configure HAL properly. Ubuntu does some HAL magic as I said above and the player works perfectly, but I use Arch now, and overall I think it's much much better, so.. help. :-)

---

### Post by hyperair on 2008-05-10
Try reading this thread: [http://www.linuxquestions.org/questions/slackware-14/how-to-get-utf8-support-for-auto-mount-by-haludev-578452/](http://www.linuxquestions.org/questions/slackware-14/how-to-get-utf8-support-for-auto-mount-by-haludev-578452/)

---

### Post by finferflu on 2008-05-10
Did you generate your locale?
You need to check /etc/locale.gen and comment out (everything else needs to be commented) the entries relevant to your locale (ar_EG.UTF-8 UTF-8 and ar_EG ISO-8859-6 perhaps?), then regenerate the locale with (as root): 

```
locale-gen
```

---

### Post by Farghal on 2008-05-10
> **finferflu said:**
> Did you generate your locale?
You need to check /etc/locale.gen and comment out (everything else needs to be commented) the entries relevant to your locale (ar_EG.UTF-8 UTF-8 and ar_EG ISO-8859-6 perhaps?), then regenerate the locale with (as root): 

```
locale-gen
```

I believe my locale is configured correctly, I don't think this is where the problem lies.


> **hyperair said:**
> Try reading this thread: [http://www.linuxquestions.org/questions/slackware-14/how-to-get-utf8-support-for-auto-mount-by-haludev-578452/](http://www.linuxquestions.org/questions/slackware-14/how-to-get-utf8-support-for-auto-mount-by-haludev-578452/)

This thread inspired me to the solution:

I right clicked the volume, went to Properties > Volume and found that the mount options included iocharset=iso8859-1. I just clicked Settings and in the Mount Options field I wrote iocharset=utf8, then unmounted and remounted the drive. It worked! Now I can read the Arabic filenames.

Thanks hyperair and finferflu. Problem #1 is now solved! (Well, kinda.. shouldn't HAL mount as UTF8 by default? At least when the locale is utf8? I believe this should be considered a bug)

About problem #2.. what does it take for Gnome to recognize a USB device as a portable mp3 player (and display it as a music source in Rhythmbox) instead of just a generic USB flash drive? Is it a HAL thing? or a Gnome/Rhythmbox thing?

Does anybody here have an MP3 player that is properly recognized as such in Arch? What did you do to make it happen?

Edit: My MP3 player is an Apacer Audio Steno AU524.

---

### Post by finferflu on 2008-05-10
> **Farghal said:**
> I believe my locale is configured correctly, I don't think this is where the problem lies.
Sorry, my mistake. I misread your above post, reading that thunar couldn't display Arabic characters, but missing it couldn't read those characters in the player :P

I'm happy you solved it, and perhaps you should address the question of UTF-8 being not used by default in the Arch forums. I admit I don't know that much about HAL. 

My MP4 player is recognised as external HD, but I don't really care, since I use plain copy-paste.

---

### Post by Farghal on 2008-05-10
> **finferflu said:**
> 
I'm happy you solved it, and perhaps you should address the question of UTF-8 being not used by default in the Arch forums. I admit I don't know that much about HAL. 

My MP4 player is recognised as external HD, but I don't really care, since I use plain copy-paste.

Me neither, my knowledge with hal ends at pacman -S hal then adding it to the demons section in rc.conf :-)

Of course I could copy and paste, but I just can't live with the idea that Ubuntu did something that Arch can't. Can you? ;-) It's also neat to have Rhythmbox handle everything related to music: Last.fm, Magnatune and Jamendo, Podcasts, MP3 players, Radio, ... etc. Oh and of course play local music :-D

---

### Post by Farghal on 2008-05-10
I solved the problem by copying Ubuntu's /usr/share/hal/fdi/information/10freedesktop/10-usb-music-players.fdi over Arch's. Now everything is detected OK.

Thanks everybody.

---

