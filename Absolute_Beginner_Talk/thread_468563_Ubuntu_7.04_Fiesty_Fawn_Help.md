---
title: "Ubuntu 7.04 Fiesty Fawn Help"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Vetona on 2007-06-09
Today I was sick of Winblows eXtra Problems on my little brothers comp, so I'm like " Hey, I should install Ubuntu on this comp ". So I did.  I am somewhat familiar with the installation process of drivers, ect.  I just use Automatix for all of my needs.  After I installed the Multimedia Drivers and Flash with Automatix I opened up Firefox to watch some music videos on YouTube.  I pulled up a song, and the video played but I heard no audio.  I checked my settings under System->Preferences->Sound and made sure my device( Logitech USB Headset ) was selected and I tested it.  I heard the beeping noise and was like weird.  So I restarted firefox and it still didnt work.  I have tried re-booting, re installing drivers, codecs, and manually install Flash 9 for Linux from there site.  None of this has worked for me. What am I missing??

--Vetona


If you want, add me on MSN or AIM:

[email]harrykjell@hotmail.com[/email]  -- MSN

Skaryharry -- AIM

---

### Post by testube_babies on 2007-06-09
These will hopefully solve your problem; they solved mine anyways :)

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)
[http://ubuntuforums.org/showthread.php?p=2787287#post2787287](http://ubuntuforums.org/showthread.php?p=2787287#post2787287)

---

### Post by Vetona on 2007-06-09
Ok.  I clicked on both links....Neither things helped me.  tell me exactly what you did on those pages that fixed your problem.

---

### Post by testube_babies on 2007-06-09
From the help site:
> Note: if sound doesn't work in Flash Player (for example on YouTube):
In a terminal, type:
sudo aptitude install alsa-oss
gksudo gedit /etc/firefox/firefoxrc

Change:

FIREFOX_DSP=""

To:

FIREFOX_DSP="aoss"

    * Restart Mozilla Firefox. Now sound should work in Flash Player. 

---

