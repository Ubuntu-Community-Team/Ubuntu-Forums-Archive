---
title: "[SOLVED] Can't read dvd's even after installing libdvdcss2?"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by drazgo on 2008-03-14
hi everyone, 

i'm having serious issues with trying to read a simple dvd (region 2 if that matters). I installed libdvdcss2, libdvdplay, libdvdnav, vlc and i even tried automatix. None worked... 

When i try to open a dvd with vlc (file->open disk->ok), vlc just shuts down. Same thing happens with totem...

any suggestions?

thanks in advance!
Drazgo

---

### Post by dje on 2008-03-14
Try running vlc from the terminal, just open up a terminal (Applications >> Accessories >> Terminal) and type:
```
vlc
```
Try to play a dvd and then post the entire output here

dje

---

### Post by drazgo on 2008-03-14
here you go: 
> 
laurens@laurens-laptop:~$ vlc
VLC media player 0.8.6c Janus

** (.:23421): WARNING **: Invalid borders specified for theme pixmap:
        /home/laurens/.themes/Mac4Lin_GTK_v0.4/gtk-2.0/Buttons/button-default.png,
borders don't fit within the image
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: The Notebook (2004) [ENG] [DVD  
libdvdnav: DVD Serial Number: 386D6C6D
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/laurens/.dvdnav/The Notebook (2004) [ENG] [DVD.map'
libdvdnav: DVD disk reports itself with Region mask 0x00400000. Regions: 1 2 3 4 5 6 8

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000011c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000849
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00007e7d
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
[00000334] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
No accelerated IMDCT transform found
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  88
  Current serial number in output stream:  89


---

### Post by dje on 2008-03-14
Ok i think it could be a problem with your graphics card (as in incompatibility),  as it mentions errors about X. Have you tried googling:
```
*your computer* ubuntu dvd
```
I'm not an expert on this so i can't help you much more than that (i may have even diagnosed it incorrectly :( ), i was just trying to get the thread going a bit. try searching and see if you get anywhere

all the best
dje

---

### Post by drazgo on 2008-03-14
well, i don't know what could possibly be the problem with my graphics card, as i haven't find any errors when i was googling the subject. i have a Dell vostro 1400 with an intel graphics card (965GM)

---

### Post by drazgo on 2008-03-14
anyone?

---

### Post by Tom--d on 2008-03-14
I know how to sort this out..

Go on

VLC > settings > preferences > Check the Advanced option > Go to video > Output modules > Then click on the drop down box and choose X11 video output > Save 

And your done!

I know this because I have the intel 965 chipset. **ALL** video will now work in vlc.

---

### Post by billgoldberg on 2008-03-14
Maybe try "ogle". You can find it in "applications -> add/remove"

I  never used it though.

Did you install your graphics card using "restriced drivers management"?

---

### Post by drazgo on 2008-03-15
tried both solutions, none did work :S @tom: is there anything i have to do on that menu of X11, cuz i don't really know what to do there...

---

### Post by forrestcupp on 2008-03-15
LOL.  *The Notebook*

> **drazgo said:**
> tried both solutions, none did work :S @tom: is there anything i have to do on that menu of X11, cuz i don't really know what to do there...

Did you get to the preferences and click the Advanced options box in the lower right side?  If so, you should be able to click on Video, then highlight 'Output modules' all on the left side, then in the drop down box that says 'Default', change it to X11.

I would think that would work.  Maybe not, though.

---

### Post by drazgo on 2008-03-15
> **forrestcupp said:**
> LOL.  *The Notebook*



Did you get to the preferences and click the Advanced options box in the lower right side?  If so, you should be able to click on Video, then highlight 'Output modules' all on the left side, then in the drop down box that says 'Default', change it to X11.

I would think that would work.  Maybe not, though.

omg, that really did work! :lolflag:thank you soooo much for helping me out! consider this topic to be solved ;)

---

### Post by forrestcupp on 2008-03-15
> **drazgo said:**
> omg, that really did work! :lolflag:thank you soooo much for helping me out! consider this topic to be solved ;)

Don't thank me.  Tom--d told you to do it.  I just explained *how* to do it.

---

### Post by drazgo on 2008-03-16
well, then thank you both! xD this community rocks!

---

### Post by 3rdalbum on 2008-03-16
Some Nvidia users will need to do this too if they get the wrong colours appearing in VLC or other video players :-)

---

