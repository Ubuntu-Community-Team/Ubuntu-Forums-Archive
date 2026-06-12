---
title: "Banshee vs Amorak"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by JEMHillcrest on 2007-12-22
Hey, im in the process of installing linux on my ipod, and I was wondering what your views were about the media player amorak vs the media player banshee. I have amorak installed as it was in the list of easily installable programs. I would like to try out Banshee, but as I am a noob at linux, I have no idea how to install it. I have the folder on my desktop but I have no clue what I should do to it. Any help or opinions would be appreciated:mrgreen:

---

### Post by tgalati4 on 2007-12-22
In a terminal:

>sudo apt-get install banshee

---

### Post by JEMHillcrest on 2007-12-22
could you give me exact commands?
Its located on my desktop, named "banshee-0.13.1"

---

### Post by PilotJLR on 2007-12-22
JEM,
It sounds like you downloaded it from the website... keep it simple, and do only what tgalati says.
That single command he posted is precisely what you need.

---

### Post by JEMHillcrest on 2007-12-22
> **PilotJLR said:**
> JEM,
It sounds like you downloaded it from the website... keep it simple, and do only what tgalati says.
That single command he posted is precisely what you need.

alright, sorry who ever posted it earlier, I didnt know what that meant. :lolflag:

---

### Post by JEMHillcrest on 2007-12-22
it worked perfectly. thank you so much. can you explain what i did exactly?

---

### Post by aysiu on 2007-12-22
> **JEMHillcrest said:**
> it worked perfectly. thank you so much. can you explain what i did exactly?
Yes. Read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Presto123 on 2007-12-22
You can also get rid of that other file you downloaded, I think. I'm meaning the one you downloaded directly from the site.

---

### Post by JEMHillcrest on 2007-12-22
alright, i got rid of old file, imported music. 
at first, it couldnt find the codecs i got for amorak for mp3's
i restarted and then i could play them
now i cant get rid of amorak
it says one or more apps depend on it. 
any1 got any suggestions on how to get rid of amorak
and also, will banshee sych with a mp3 playa (ipod with linux os on it)?

---

### Post by JEMHillcrest on 2007-12-22
I got 1 more ??
will banshee play video padcasts or just strait up videos of any sort?
that whould make it bomb

---

### Post by Martje_001 on 2007-12-22
Go to: System --> Administration --> Synaptic and search for 'Amarok'. Delete it; confirm if it wants to delete other things.

Btw: Synaptic is an Graphical User Interface for apt-get. You can install almost everything with Synaptic (and, of course) delete it.

---

### Post by tgalati4 on 2007-12-22
Banshee will only do music, no videos.  There may be a plug-in to do video in the future.  It's in constant development, so you may see it in a future version.  Check the banshee website for developments.

---

### Post by JEMHillcrest on 2007-12-22
> **Martje_001 said:**
> Go to: System --> Administration --> Synaptic and search for 'Amarok'. Delete it; confirm if it wants to delete other things.

Btw: Synaptic is an Graphical User Interface for apt-get. You can install almost everything with Synaptic (and, of course) delete it.

alright, i got all the way till you search, i search for it, and a folder comes up called amorak. it says that , under amorak, there are 0 packages, broken, install/upgrade, and 0 to remove, only thing that has number for it is installed, 1184, so i cant delete anything or watever i was gonna do

---

### Post by tgalati4 on 2007-12-22
Right-click on the amarok check-box and click uninstall.  Then hit apply.  

Personally I would leave Amarok, since it has some neat features as well.  It doesn't hurt to keep both banshee and amarok since they are completely different architectures.

---

### Post by JEMHillcrest on 2007-12-22
i got rid of banshee, it had too many problems for me, just 1 last ??, will amorak synch with a linux-ipod

---

### Post by FreewheelinFrank on 2007-12-22
*Amarok.*

"Amorak" sounds a bit too much like anorak.

Which is the 3rd uncoolest word in the English language.

---

### Post by tgalati4 on 2007-12-23
You get a better user experience keeping the Apple firmware on your iPod and using gtkpod for loading music onto your iPod and Amarok for playing music from your iPod on your computer.

Linux on the iPod is a way to get games and other Linux capability onto the iPod, but playing music and battery life suffer.  If you want to experiment, try Rockbox instead.

---

