---
title: "external mic not working"
date: 2011-06-26
forum: Apple Hardware Users
---

### Post by goneskiing on 2011-06-26
The external mic (audio technica lavalier) is not working on my white 13" macbook - all I'm getting is low volume from the built-in mic picking up my voice.  

are my settings right ?

1) there are 2 unmarked plugin holes - the frontmost has a red light shining in it - it works with my headphones - I assume the 2nd plug is for the mic

2) running gnome-alsamixer I always notice the mic jack box is unchecked and when I check it it gives a response "no idea what to do with mixer element mic jack mode"

3) running alsamixer (under kubuntu) and tabbing for capture the mic columns have no bars - I assume they should be set for mic in and not line in ?  

4) using Audacity I have set it for pulse mic 1 not mic 0 (which I assume should be internal mic ?)  (I also tried default with no success)  

5) under /etc/modprobe.d/alsa-base.conf I have added the line:
options snd-hda-intel model=mb5

thks for any help

---

