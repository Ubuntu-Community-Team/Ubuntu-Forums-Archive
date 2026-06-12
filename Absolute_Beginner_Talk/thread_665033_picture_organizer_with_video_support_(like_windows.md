---
title: "picture organizer with video support (like windows picasa)"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by quickk on 2008-01-11
Hi Everyone, 

   I really like ubuntu 7.10, however there is one thing that is driving me crazy.  I've been looking for days for a simple picture organizer which can also display video files.  Picasa for windows does this very well.  

Is there any hack available so that the linux picasa can see video files?

I've tried installing the windows picasa version with wine, but it didn't work.  Has anyone successfully done this (and got video display to work)?

Does anyone have any suggestions?  

Thanks!

---

### Post by santiagoward2000 on 2008-01-11
> **quickk said:**
> Hi Everyone, 

   I really like ubuntu 7.10, however there is one thing that is driving me crazy.  I've been looking for days for a simple picture organizer which can also display video files.  Picasa for windows does this very well.  

Is there any hack available so that the linux picasa can see video files?

I've tried installing the windows picasa version with wine, but it didn't work.  Has anyone successfully done this (and got video display to work)?

Does anyone have any suggestions?  

Thanks!

Well, I've been using Picasa for Linux (which is basically Picasa for Windows wrapped with wine, but works better than installing the Windows version yourself) and works quite well with most videos (except for Quicktime videos).
If you want you can give it a try:
[http://picasa.google.com/linux/]("http://picasa.google.com/linux/")
Cheers!

---

### Post by quickk on 2008-01-11
Thanks for the reply!  I had used Picasa before but didn't notice that they added support for video files!  

I just tried it, and my video files do show up in the thumbnail preview mode but when I click to view a video, all that I get is a black box, no sound.  My video files are created with a canon SD800 camera.  It makes some sort of avi file (I think that the video compression has to do with jpegs or something).  

Are you actually able to play the files from within picasa?

---

### Post by santiagoward2000 on 2008-01-12
> **quickk said:**
> Thanks for the reply!  I had used Picasa before but didn't notice that they added support for video files!  

I just tried it, and my video files do show up in the thumbnail preview mode but when I click to view a video, all that I get is a black box, no sound.  My video files are created with a canon SD800 camera.  It makes some sort of avi file (I think that the video compression has to do with jpegs or something).  

Are you actually able to play the files from within picasa?

Hi!
Sorry, but right now all my videos are .mov, so they don't work with Picasa. I remember Picasa read the .avi files I had before, but never tried to play them.

---

### Post by josh92176 on 2008-01-12
Try DigiKam (go applications add/remove) It works in gnome and KDE. I think it works with .mow files. Might not though.

-josh

---

### Post by Nerdtoknow on 2008-04-05
I'm having a problem that no video files show up in Picasa 2.7.  I'm using Ubuntu 7.10.  
I have one folder with 10 or so MPG files, and another with .AVI files.  Both folders are selected in Picasa for Scan Always.  There are some JPG files in the folders and they get picked up just fine.

Any ideas?

N

---

### Post by Doorslammer on 2008-04-05
are you able to view video files in other programs ? 
did you install the restricted-extras 
which installs all codecs  ?

---

### Post by Nerdtoknow on 2008-04-07
Yes, I can view movies with other viewers.

I don't know about the restricted extras so I obviously haven't loaded them. 

What are they and where can I get them?

Thanks,

N

---

### Post by Nerdtoknow on 2008-04-07
More Info:

I checked the Synaptic Package Manager and it says the Ubuntu-restricted-extras are loaded.

:confused:

N

---

### Post by SunnyRabbiera on 2008-04-07
you enable more repositories, by going into synaptic and going into settings.
synaptic is in system>administration>synaptic.
in its settings you can add extra repositories by clicking on the boxes in the first tab (check all but the final one)

edit: okay you may also want to add the medibuntu repositories:
[read the instructions here]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by Nerdtoknow on 2008-04-07
I'm still stumped.  I checked and I have the extra repositories loaded and Mplayer is loaded.

Yet, when I browse my folders with Picasa neither my .avi or .mpg files even show up.  In fact, I have one folder that only has .MPG files in it, and the folder doesn't even show up. 

I'm on Picasa 2.7, build 37.611,0 for Linux.

Any more ideas anyone?

thanks,

N

---

### Post by Nerdtoknow on 2008-04-07
I just tried double clicking on the actual video files in Nautilus.  the Program that opened them and played them properly is called Totem Movie Player 2.20.0.
It says it uses GStreamer 0.10.14 and GNOME.

Does this explain anything?

N

---

