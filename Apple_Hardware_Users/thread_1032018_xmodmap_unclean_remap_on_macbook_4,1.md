---
title: "xmodmap unclean remap on macbook 4,1"
date: 2009-01-05
forum: Apple Hardware Users
---

### Post by SaiHayashi on 2009-01-05
Hi all,

I've been using xmodmap to swap the alt and cmd key on my macbook 4,1. it sort of does what i want, as when i test it on xev where it should be alt_L returns super_L and vice versa.

however, when i combo the new super_L with and another key, say i wanna do a "super_L + tab" to execute ring application switch, it would execute "alt_L + tab" and execute the static application switcher (the new alt_L works perfectly as i wanted).  i have tried to manually map the ring switcher key to new super_L + tab, but as i press that, it is recognised as alt + tab, whereas if i press new super_L alone, it is recognised as super.

now this type of behaviour i would say is unclean, and i would want to fix it.

thanks in advance.

kelvin

N.B. as most of us macbook users experience the low volume problem with alsamixer, i have noticed that after i followed the installation guide of skype from [ubuntu community wiki]("https://help.ubuntu.com/community/Skype"), by doing the following to install esound
```
killall pulseaudio
sudo aptitude remove pulseaudio
sudo aptitude install esound
sudo aptitude remove /etc/X11/Xsession.d/70pulseaudio
```
i have a louder volume coming out of the speaker.
if anyone can verify that it does work, feel free to add that up to the wiki.

---

