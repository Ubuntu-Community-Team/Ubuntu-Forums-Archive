---
title: "[SOLVED] how do I play my dvd newbie alert"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by playme123 on 2007-07-11
hi
whenever I go to play dvd in totem I get the following message
Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.
Im totally new and feeling a bit lost all help would be appreciated:(

---

### Post by Nameless_one on 2007-07-11
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability)

Generally, ubuntuguide will solve most of your issues in the beginning. Check it out.

---

### Post by overdrank on 2007-07-11
> **playme123 said:**
> hi
whenever I go to play dvd in totem I get the following message
Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.
Im totally new and feeling a bit lost all help would be appreciated:(

Hi maybe this link will help
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Good luck! :popcorn:
Nice avatar nameless!

---

### Post by playme123 on 2007-07-11
im getting more confused by the minute

---

### Post by overdrank on 2007-07-11
> **playme123 said:**
> im getting more confused by the minute

I understand, I too was confused and still am at times. But I you like  a challenge and like to solve and learn new things it can be a great experience. Just take a deep breath and you can always ask for help. :)

---

### Post by Nameless_one on 2007-07-11
Ask and thou shalt receive an explanation :)

---

### Post by playme123 on 2007-07-11
headache coming on now, how do I and what do I do to get the plugins for totem

---

### Post by mr_biggie on 2007-07-11
just go to synaptic and install the gstreamer plugins.

---

### Post by Nameless_one on 2007-07-11
1) You have to enable extra repositories from which you can install programs with apt-get and aptitude (which manage your programs and help you install and remove them). To do that:

 * Go to the menu: System -> Administration -> Software Sources
 * check everyhting on the first tab. 

2) Now, open a terminal (Alt+F2, type gnome-terminal and press Enter) and paste the following commands, one by one: ```
sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo apt-get install totem-xine
sudo apt-get install libdvdcss2
```

That's it. By the way, all I did was explain what was in the link I posted. Maybe you should also check this link too: 

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

everything is explained very plainly, and it will get you started.

---

### Post by hyper_ch on 2007-07-11
and you need to get libdvdcss2 (it's available from the medibuntu repository; google for medibuntu and follow the howto on how to add that one to your computer)

---

### Post by playme123 on 2007-07-11
done that and it still aint working

---

### Post by hyper_ch on 2007-07-11
you added the medibuntu repo and then you installed libdvdcss2?

---

### Post by moredhel on 2007-07-11
you could install vlc :)

---

### Post by hyper_ch on 2007-07-11
withough libdvdcss2 vlc doesn't help much either ;)

---

### Post by playme123 on 2007-07-11
can someone give me a step by step guide in a dummy version cos im not getting it at all I know you are all trying to help

---

### Post by carloslosgrande on 2007-07-11
Hi, have you tried your top panel  >'applications'> 'add/remove' ?
when this loads go to the top right menu window called 'show' and select 'all available applications'
then go to the search menu and look for 'codecs'
you should get stuff like 'gstreamer' plugins/codecs.
select them and click on 'apply'

Then Bob's your uncle.

---

### Post by playme123 on 2007-07-11
done that and it still isnt working

---

### Post by lisati on 2007-07-11
> **playme123 said:**
> done that and it still isnt working

Here's another "how to": [https://help.ubuntu.com/7.04/musicvideophotos/C/video.html](https://help.ubuntu.com/7.04/musicvideophotos/C/video.html)

---

### Post by hyper_ch on 2007-07-11
what did you do?

---

### Post by playme123 on 2007-07-11
I installed the gstreamer codecs

---

### Post by playme123 on 2007-07-11
anyone

---

### Post by hyper_ch on 2007-07-11
what about libdvdcss2?

---

### Post by playme123 on 2007-07-11
[http://www.getautomatix.com/](http://www.getautomatix.com/)
was given this link buy someone downloaded it, installed the vlc media player and am now watching my dvd, thank god the pc was nearly out of the window at one point

---

### Post by playme123 on 2007-07-11
> **playme123 said:**
> [http://www.getautomatix.com/](http://www.getautomatix.com/)
was given this link buy someone downloaded it, installed the vlc media player and am now watching my dvd, thank god the pc was nearly out of the window at one point
also have installed the codecs and plugins for totem from automatix and its all working now, who ever made this prgram is a god and thanks for all your help guys even though I didnt have a clue what I was doing:)

---

