---
title: "ALSA: wtf?"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by johnnyw on 2007-06-09
hi there, i ve been trying to configure my sound in 6.06 trying to follow  the alsa project spread sheet that is supossed to be for my Sound card ( i have a Audio
	

# Realtek ALC650
# AC'97 2.2 S/PDIF extension compliant codec
# Supports Microsoft® DirectSound/DirectSound 3D
# AC&#8217;97 supported with full duplex, independent sample rate converter for audio recording and playback
# S/PDIF-in/out interface
# 6-channel audio output

)
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=ATI&card=ATI-IXP+southbridge+AC97+audio.&chip=IXP+SB150%2C+IXP+SB200%2C+IXP+SB250%2C+IXP+SB300%2C+IXP+SB400&module=atiixp#intro](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=ATI&card=ATI-IXP+southbridge+AC97+audio.&chip=IXP+SB150%2C+IXP+SB200%2C+IXP+SB250%2C+IXP+SB300%2C+IXP+SB400&module=atiixp#intro)

I am a complete nood in linux and cant follow the way things are explained right there, apart from that, English is not my native Language . Can someone provide me some help please?

Thanks in advance

J

---

### Post by ggaaron on 2007-06-09
If you are new to linux, then why are you not using the latest version? 6.06 is mainly for servers because of it's LongTimeSupport, but installing newer version often solves many problems.

---

### Post by johnnyw on 2007-06-09
I do not know how to programme and all that stuff. i have 6.06 and received in my mail the 7.07 but have been told not to upgrade as I should first update to 6.1 and afterwards to 7.07.

Not trying to be nasty, but are you willing to help or just to question me?

Thanks

J

---

### Post by durrell on 2007-06-09
I think he's saying an upgrade would be the easiest way to fix your problem without having to change your settings..

Basically, if you don't upgrade you're going to need to open a Terminal window and run the commands on that page. First:
```
modinfo soundcore
```

Then if it gives you a message saying you have that module already, then you don't need to recompile your kernel. The rest of the commands can be copied and pasted into the terminal. Pretty straightforward, really..

---

### Post by ggaaron on 2007-06-09
I just wanted to say that probably with older version you will have other problems. I would suggest a new install of Feisty not upgrade, but sorry - this isn't an answer for your question.

I don't know how to help you, but probably this guide you posted is not needed. I think that ubuntu has alsa installed by default, if not you should install it using apt-get (or synaptic). I don't think that alsa has to be configured so much. You have to install latest alsa, latest kernel (to insure that your audio card is supported - it really should be), run alsamixer - unmute channels and try to play something for example with mplayer.

---

### Post by johnnyw on 2007-06-09
should I keep pasting the stuff under "modinfo soundcore" ?

as i do not know what cvs are I did not know wether I should use that "solution" for my problem as listed there

Been trying to follow the steps but come with this:

cp: cannot stat `/downloads/alsa-*': No such file or directory

---

### Post by durrell on 2007-06-09
Try opening up terminal and typing alsamixer. It would look something like this:

[IMG]http://img.photobucket.com/albums/v157/Durrell12/Screenshot-2.png[/IMG]

If you can't open it, then you know you need to install it. It should be installed by default. I still think you'd be better off to do a fresh install of Feisty (7.04).

---

### Post by johnnyw on 2007-06-09
thx dude..

mine looks pretty shitty compared to yours

[[IMG]http://img501.imageshack.us/img501/8341/screenshot2sk7.th.png[/IMG]](http://img501.imageshack.us/my.php?image=screenshot2sk7.png)

---

