---
title: "Sound.."
date: 2005-05-15
forum: Absolute Beginner Talk
---

### Post by animesh on 2005-05-15
my xmms and mplayer both are working properly on ubuntu but there is no sound 
not even in the gaim messenger ;on linux thr is no sound but in windows xp everything is working properly

---

### Post by Dave88 on 2005-05-15
go into system>preferences>multimedia systems selctor and try changing the audio systems.

---

### Post by animesh on 2005-05-16
thnks 4 the reply but plz can u tell me where is this system .....in which preferences are there?
I have been able to find system tools and system configuration only

---

### Post by Stormy Eyes on 2005-05-16
[QUOTE=animesh]thnks 4 the reply but plz can u tell me where is this system .....in which preferences are there?
I have been able to find system tools and system configuration only[/QUOTE]

He already did. "system>preferences>multimedia systems selctor" means the following:

[indent]1. Open the **System Menu** in GNOME.
2. Open the **Preferences** submenu.
3. Select **Multimedia Systems Selector**.[/indent]

Once there, switch your audio systems to **ALSA**.

---

### Post by animesh on 2005-05-23
well i think there is a difference in notation because i have found out where sound is,its in the desktop preferences and this desktop preferences was in computer and it was there in my panel . 
     
   Apart from that now my mplayer is giving sound but gaim and other events such as error,log in etc. are still soundless whereas in sound in sound events all of these are there that is from my side i have enabled for a sound to be produced on the events given in Sound events 
                        thanks in advance

---

### Post by poofyhairguy on 2005-05-23
[QUOTE=animesh]well i think there is a difference in notation because i have found out where sound is,its in the desktop preferences and this desktop preferences was in computer and it was there in my panel . 
     
   Apart from that now my mplayer is giving sound but gaim and other events such as error,log in etc. are still soundless whereas in sound in sound events all of these are there that is from my side i have enabled for a sound to be produced on the events given in Sound events 
                        thanks in advance[/QUOTE]

[http://www.ubuntuforums.org/showthread.php?t=26567&highlight=sound](http://www.ubuntuforums.org/showthread.php?t=26567&highlight=sound)

[http://www.ubuntuforums.org/showthread.php?t=32063&highlight=sound](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=sound)

read them in that order.

---

### Post by animesh on 2005-05-23
i think i have made some terrible mistake . the link said kill esd i did that but with that i also did the following

               rm /dev/snd/controlC0
               rm /dev/snd/controlC1
               rm /dev/dsp

               gedit /etc/esound/esd.conf( i changed it to as given in the link)


        after doing this i am getting the following error
              
Segmentation fault

You've probably found a bug in XMMS, please visit
[http://bugs.xmms.org](http://bugs.xmms.org) and fill out a bug report.

---

