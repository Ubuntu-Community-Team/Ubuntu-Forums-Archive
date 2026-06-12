---
title: "all i want for x-mas is to play a f****** DVD"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by miller3790 on 2006-08-24
i've been sitting here for 3 hours trying to play a DVD and NOTHING that i've tried works. And its not like i'm not an intellegent person here. I work in IT at a hospital so i know my way around computers. This is however my first linux endevor. When i open Totem and tell it to play the dvd it comes up with the error: **Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.** Pleas install the necessary plugins and restart Totem to be able to play this media. Anyone out there who can help now's your time to shine. I appreciate whatever i can get. Thanks

---

### Post by hopstah on 2006-08-24
try ```
sudo apt-get install libdvdcss2
```or search google for easyubuntu and install and run that.

---

### Post by Catewilliams on 2006-08-24
I have the same problem, but I have Easyubuntu installed. I found that Totem didn't want to read the DVD, but would read the cd instead..? Anyways, it ended up working for me. 

Also, I tried Hopstahs advice, and that seemed to work for me. Best of luck!

---

### Post by Frank Golden on 2006-08-24
> **Catewilliams said:**
> I have the same problem, but I have Easyubuntu installed. I found that Totem didn't want to read the DVD, but would read the cd instead..? Anyways, it ended up working for me. 

Also, I tried Hopstahs advice, and that seemed to work for me. Best of luck!
Try installing XINE. For me works much better than Totem.

---

### Post by Metacarpal on 2006-08-24
Using Xine, Gxine, or Totem-Xine is the best way to watch DVDs in Ubuntu that I've found so far.  Totem-gstreamer can play them, but you won't have menus.

However, to get DVDs going in any of them, you will need to [install an additional package or two]("https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9").

The reason for this is that the encoding on DVDs is not an open format - it's copyrighted, or patented, or somesuch.  The licensing to use the patent is sold in two parts: first to the people making DVDs, then to the people making DVD players (or, in the computer world, DVD-playing software).

Because Ubunutu is commited to using only free (not just gratis {free as in free beer} but also libre {free as in freedom / open source}) software, the codecs/plugins necessary to play DVDs are not included in the initial installation.  It's up to the end user to decide whether s/he wants those files on the computer, and install them (using the directions in my link above, or an installer like EasuUbuntu or Automatix).

---

### Post by xpod on 2006-08-24
> Try installing XINE. For me works much better than Totem.

I tried that..NOW ive got another app that sound is missing from.Had the flash sound prob and the sys sound prob and NOW ive got the same pleasure
with yet another piece of the jigsaw........alsa?,also-oss,codecs,no codecs,ecd,via etc etc......mix them all up and what do you get...

One confused bloody scotsman.....Could be worse i suppose,could be yet another virus/ad/spyware program i was  having trouble with on "THAT" hd:D 

My kids have a real jigsaw that say`s "from 4-5 years" on the side of it but i done it in 3....SO im sure i`ll pick THIS up eventually eh.lol...:tongue:

Off to watch some buster keaton movies on my silent movie player

---

### Post by pdobrev on 2006-08-24
Give ogle a try.

sudo apt-get install ogle ogle-gui

It has menus support and plays DVDs quite nicely. The only thing I haven't yet figured out is how to change camera angles.

---

### Post by Catewilliams on 2006-08-24
> **pdobrev said:**
> Give ogle a try.

sudo apt-get install ogle ogle-gui

It has menus support and plays DVDs quite nicely. The only thing I haven't yet figured out is how to change camera angles.


Ogle seems to work great! Thanks for the advice!


> 
with yet another piece of the jigsaw........alsa?,also-oss,codecs,no codecs,ecd,via etc etc......mix them all up and what do you get...

Alsa is a sound mixer, I believe. I have it, because I use Ventrilo and it makes it work nicer. If you use synaptic, you can search for Alsa and it should show up.  The UbuntuWiki should have definitions of the other things you are confuzed about. ^^ I wish you luck!

---

### Post by tomekpilot on 2006-08-24
... install AUTOMATIX:

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_Automatix](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_Automatix)

... then you'll be able to install all the codecs and whatnot. Works like a charm.

---

### Post by Buzzygirl on 2006-08-25
I'm having the same problem here on my boyfriend's computer. I downloaded Ogle, but every time I put in a DVD and have Ogle running, I keep getting an error message that "TOTEM could not play dvd:///media/cdrom0, no URI handler implemented for 'dvd'". 

I can't get it to work in Xine either. Keeps reverting to Totem errors and I can't get Totem to play anything on this computer. ??

---

### Post by Bachstelze on 2006-08-25
All you guys need is [here](https://help.ubuntu.com/community/RestrictedFormats).

---

### Post by Buzzygirl on 2006-08-25
I downloaded the extra libraries as instructed above (thanks, I'm still weak with the command line) and finally got Xine to play "Hunt for Red October" just fine. I can't get a picture (but I do get sound) when I attempt to play a new DVD of CSI Miami.

---

### Post by Buzzygirl on 2006-08-25
Well, now I got my DVDs to work through Xine (still no Totem, so forget it) and I don't really know HOW I got it working, but I played around a bit and voila. Thanks for the link to Restricted Formats, it's exceedingly helpful!

---

### Post by Bachstelze on 2006-08-26
If you like Totem, just install totem-xine and it will play in it too :)

---

### Post by barranco on 2006-08-26
I didn't had any luck getting any DVDs to play but unencrypted then reboot and finally I could get the encrypted DVDs to play so I was happy camper, then when out for a while turned off the computer and when I came back I couldn't play DVDs again, that was weird so I did a couple of more test and found out that it will only play encrypted DVDs if the computer was booted with a dvd movie inside.

so I guess there is something that doesn't at boot time :confused:

---

### Post by Skia_42 on 2006-08-26
make sure that you are trying to play legitimate dvds, I have had problems playing copied dvds on my computer so please bear that in mind...

---

### Post by barranco on 2006-08-26
> **Skia_42 said:**
> make sure that you are trying to play legitimate dvds, I have had problems playing copied dvds on my computer so please bear that in mind...

oh I have no problem playing back copied DVDs, only legitimates.

---

### Post by ¤&#1712;pï&#345;&#359;&#64417;&#940;&#950;¤ on 2006-08-26
Unfortunately, Xine does not support DVD menus directly; however, there is a plugin called dvdnav (available from [http://prdownloads.sourceforge.net/dvd](http://prdownloads.sourceforge.net/dvd)) that adds this functionality to Xine. This plugin is a must-have if you intend to use Xine for DVD playback. The plugin works very well, even with the complex animated menus that some DVDs have, and although this is not required for DVD playback, it obviously gives you complete access to all the features available. The code for the DVD navigation was written referencing the original Ogle DVD menu code base.

source: [http://www.linuxjournal.com/article/5644](http://www.linuxjournal.com/article/5644)

---

### Post by madscientist on 2006-08-29
> **Buzzygirl said:**
> I'm having the same problem here on my boyfriend's computer. I downloaded Ogle, but every time I put in a DVD and have Ogle running, I keep getting an error message that "TOTEM could not play dvd:///media/cdrom0, no URI handler implemented for 'dvd'". 

I can't get it to work in Xine either. Keeps reverting to Totem errors and I can't get Totem to play anything on this computer. ??FYI, to avoid "reverting to Totem" you should go to System -> Preferences -> Removable Drives and Media, then click the "Multimedia" tab.  You'll see the command invoked whenever a new DVD is inserted into the drive, which will be something like "totem %m".  You can uncheck the box so Ubuntu won't try to do anything fancy at all with a newly-inserted DVD; you'd just run your player by hand.  Or, you can replace "totem %m" with whatever command you use to watch a movie.  If you've installed xine you can use "xine dvd://" (worked for me anyway).

---

### Post by Buzzygirl on 2006-08-29
Fantastic! Just what I was looking for. Thanks!

---

