---
title: "[SOLVED] three problems left - help appreciated!"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by n00rt on 2008-02-06
Hi - I've recently come back to ubuntu after a bit of a hiatus - i was on edgy back last year sometime and i've gotta say the gutsy version has fixed almost all the bugs that i had back then (intel wireless being the major problem back then)

but,

there are three things that are getting me down that i need help with - any suggestions or tutorials / links etc would be great. - here goes.

1. how can i keep my windows partition mounted when i boot up - at the moment any time i need a file from this partition i have to first mount the disc and type my password. only a slight annoyance but it messes up my desktop so i would like to fix it.

2. when i insert a cd/dvd it says that the device is unaccesible / unauthorised and doesn't work but i can then open the files from the mounted cd that appears on the desktop and use them from there - any way to get this to work automatically?

3. this is the main problem.  the volume of anything i play, from any application is unaffected by both the volume control in the taskbar at the top and the volume buttons on my laptop.  sound card is some realtek thing that came with cheap laptop. 
I really need to get this sorted so thanks in advance for any help

---

### Post by emarkd on 2008-02-06
1.  This guide may help:  [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

2.  No idea.  Sorry.

3.  Sometimes the Volume Manager sets itself up for the wrong device.  Right-click on the volume manager and select Properties.  You should see a drop-down box for devices.  Just select another one and see if your volume control works now.

---

### Post by n00rt on 2008-02-06
hi - re the volume manager - no joy i'm afraid.  i think its something to do with my alsa set up but i'm still trying to get my head round it!

---

### Post by emarkd on 2008-02-06
Did you try

```
alsamixer
```

from the terminal?

---

### Post by n00rt on 2008-02-06
hi - sorry i have sorted it now thanks - didn't see the pcm in the list - in alsamixer it was in the red and unaffected by the slider so i swapped to pcm and it works.  anyone know what pcm stands for?

1 down - i'll check that link for mounting the drive now - Thanks!

---

### Post by GV1pJTHl on 2008-02-06
> **emarkd said:**
> Did you try

```
alsamixer
```

from the terminal?
Or if you prefer something on your menu that is a 'GUI' (although a little bit old school):
user@machine ~> sudo aptitude install alsamixergui

In Xubuntu it appears under the Multimedia menu can't speak for gnome or kde.

---

### Post by SOULRiDER on 2008-02-06
For question #2
[https://help.ubuntu.com/ubuntu/desktopguide/C/video.html](https://help.ubuntu.com/ubuntu/desktopguide/C/video.html)

---

### Post by n00rt on 2008-02-06
thanks again to emarked! - found a link in the link you suggested for keeping windows partition mounted using the ntsf-config tool - i had tried it before but as i had manually mounted the drive before using ntsf-config it didn't work.  Now it does and i'm down to 1 problem left - the cd drive.  I shall try the link above from SOULRiDER.

---

### Post by n00rt on 2008-02-06
Hey - the thread helped.  Wow thats all three problems solved in an hour!

thanks to everyone!

---

### Post by perlluver on 2008-02-06
Please mark as solved, in the thread tools at the top of the posts.

---

