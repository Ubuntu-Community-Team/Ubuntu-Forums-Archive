---
title: "can't install &quot;ugly&quot; plugins"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by dabigguy85 on 2008-04-04
I'm trying to update to get mp3 compatability and it's saying I need to remove conflicting software first in the synaptic package manager.  How do I do this?

---

### Post by Bubba64 on 2008-04-04
Give us some more info what distribution are you running and have you installed Totem xine and have you gone into software sources and opened more repositories than just a down load enables and post the conflicting software info. This will get you farther along with getting some help

---

### Post by drascus on 2008-04-04
umm what version of ubuntu are you running. Software can be removed from synaptic by going to System->administration->Synaptic manager. search for the conflicting software right click the check box of the software package and select complete removal. then click apply. Then you should be able to install the plugin. 

Note: MP3 plugins are not legal in all locations please check and make sure that you are not in a location where software patents are preventing you from using MP3 formats.

---

### Post by mcduck on 2008-04-04
Just go to Synaptic and then try to install those plugins from there. If it needs to remove any conflicting packages it will tell you so, and handle everything automatically. You don't need to find those conflicting packages yourself.


Anyway, support for MP3 is not in the "ugly" package. "Ugly2 contains "not perfectly working" codecs and other stuff, most users probably won't ever need it. I think MP3-support is in either the "good" or perhaps in the "bad" package. Also, make sure you have universe&multiverse repositories enabled, and use the multiverse-versions of gstreamer plugin packages if you want  the best support for different media formats.

---

### Post by Bubba64 on 2008-04-04
> **mcduck said:**
> Just go to Synaptic and then try to install those plugins from there. If it needs to remove any conflicting packages it will tell you so, and handle everything automatically. You don't need to find those conflicting packages yourself.


Anyway, support for MP3 is not in the "ugly" package. "Ugly2 contains "not perfectly working" codecs and other stuff, most users probably won't ever need it. I think MP3-support is in either the "good" or perhaps in the "bad" package. Also, make sure you have universe&multiverse repositories enabled, and use the multiverse-versions of gstreamer plugin packages if you want  the best support for different media formats.

+1

---

