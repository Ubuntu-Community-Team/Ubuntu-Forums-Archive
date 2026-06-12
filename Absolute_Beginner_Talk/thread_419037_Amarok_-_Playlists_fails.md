---
title: "Amarok - Playlists fails"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by U5tabil on 2007-04-22
My playlists in Amarok just fails to start. Even when i make new playlists it fails to load.

First it says in the bar: 
Some media could not be loaded (Not playable)

Then it says:
These media could not be loaded into the playlist: 
file:///home/u5/.kde/share/apps/amarok/playlists/CD's.m3u

If i try to make a new playlist with another name the same error occurred.

Anyone know why? Iv tried to install it over and over again but the same error always pop up. :confused:

---

### Post by AndyCooll on 2007-04-22
Probably best to delete your Amarok settings folder. Backup your playlists etc first. You can find them as sub-folders within the Amarok folder. To remove do the following:

```
rm -R ~/.kde/share/apps/amarok
```

Then try starting up Amarok again.

:cool:

---

### Post by U5tabil on 2007-04-22
> **AndyCooll said:**
> Probably best to delete your Amarok settings folder. Backup your playlists etc first. You can find them as sub-folders within the Amarok folder. To remove do the following:

```
rm -R ~/.kde/share/apps/amarok
```

Then try starting up Amarok again.

:cool:

Hey. Thanks it seems to be working just fine now :popcorn: 

You know why things where ****** up? 
Now i know what to do next time, if it should happen again.

---

### Post by U5tabil on 2007-04-22
Arh it aint working... after loading my enire collection my playlist didn't work again... :confused:

---

### Post by U5tabil on 2007-04-23
no one knows why this happens?

---

### Post by U5tabil on 2007-04-23
oh i am getting so mad about Amarok not being able to load my playlists! ](*,)

---

### Post by petersjm on 2007-04-23
> **U5tabil said:**
> oh i am getting so mad about Amarok not being able to load my playlists! ](*,)

Sounds to me like you could have a codec problem with .m3u files. Hang on, I'll see if I can track something down...

---

### Post by U5tabil on 2007-04-23
> **petersjm said:**
> Sounds to me like you could have a codec problem with .m3u files. Hang on, I'll see if I can track something down...

THANK YOU THANK YOU SO MUCH!!! :)

---

### Post by petersjm on 2007-04-23
> **U5tabil said:**
> THANK YOU THANK YOU SO MUCH!!! :)

I can't find anything relevant at the minute. Do you have all the prerequisite codecs installed? If you have Automatix2 installed, make sure you install all the media codecs from it. Not sure if that's your problem, but it's worth a shot. If you haven't found the answer by tomorrow, I'll keep looking.

---

### Post by U5tabil on 2007-04-24
> **petersjm said:**
> I can't find anything relevant at the minute. Do you have all the prerequisite codecs installed? If you have Automatix2 installed, make sure you install all the media codecs from it. Not sure if that's your problem, but it's worth a shot. If you haven't found the answer by tomorrow, I'll keep looking.

Well i have just installed amarok like apt-get install amarok nothing more... But i have installed all the video codecs and so on to play all the video files for mplayer. Strange if suddendly after half a year of using and installing ubuntu that the codec shouldn't be installed.

can't find anything about automatix in apt-get... what is the name of the codecs?

---

### Post by petersjm on 2007-04-24
Okay, I've done some digging about m3u files. I made a mistake in thinking it was a media file (like ogg or mp3). It's actually just a text file that stores the running order of your songs - your playlist. So having codecs is not your problem. I'm afraid I'm at a loss as to why they aren't working. Maybe either the files are corrupt, somehow, or there's something wrong with your install of Amarok. I'd suggest deleting Amarok (sudo aptitude --purge remove amarok) and reinstalling - but using the version from Amarok's website (here: [http://amarok.kde.org/wiki/Download:Kubuntu](http://amarok.kde.org/wiki/Download:Kubuntu) ). Hope that helps.

---

### Post by U5tabil on 2007-04-24
> **petersjm said:**
> Okay, I've done some digging about m3u files. I made a mistake in thinking it was a media file (like ogg or mp3). It's actually just a text file that stores the running order of your songs - your playlist. So having codecs is not your problem. I'm afraid I'm at a loss as to why they aren't working. Maybe either the files are corrupt, somehow, or there's something wrong with your install of Amarok. I'd suggest deleting Amarok (sudo aptitude --purge remove amarok) and reinstalling - but using the version from Amarok's website (here: [http://amarok.kde.org/wiki/Download:Kubuntu](http://amarok.kde.org/wiki/Download:Kubuntu) ). Hope that helps.

Ok il try that. But i use Ubuntu not Kubuntu, isn't there any difference? Gnome vs KDE?

---

### Post by petersjm on 2007-04-24
No, there's no difference. It's just that Amarok is a KDE app, therefore they list it as available for Kubuntu. It works just the same in Gnome. Good luck and keep us informed.

---

### Post by U5tabil on 2007-04-24
> **petersjm said:**
> No, there's no difference. It's just that Amarok is a KDE app, therefore they list it as available for Kubuntu. It works just the same in Gnome. Good luck and keep us informed.

Ok i did as you said and did the part from that site. but it still fails.... This is very strange...

---

### Post by petersjm on 2007-04-24
> **U5tabil said:**
> Ok i did as you said and did the part from that site. but it still fails.... This is very strange...

Strange. Could be corrupt m3u files, then. Did you import them from another OS/device/application, or create them in Amarok? Can you create another one and see if that works?

---

### Post by U5tabil on 2007-04-24
> **petersjm said:**
> Strange. Could be corrupt m3u files, then. Did you import them from another OS/device/application, or create them in Amarok? Can you create another one and see if that works?

It fails even when i make an entirely new list. Even after reinstalling the program. so thats why it is so strange. i can create new playlists but then they fails loading them. 

The only time they work is when i deleted the folder you said earlier and then make a playlists, then they work, but they fail as soon as i have rescanned my entire collection....:confused:

---

### Post by petersjm on 2007-04-25
I'm at a loss as to what the problem is now. Maybe if you head over to Amarok's forums ([http://amarok.kde.org/forum/](http://amarok.kde.org/forum/)) and ask there? Hopefully someone else will have the answer. Good luck.

---

### Post by U5tabil on 2007-04-25
> **petersjm said:**
> I'm at a loss as to what the problem is now. Maybe if you head over to Amarok's forums ([http://amarok.kde.org/forum/](http://amarok.kde.org/forum/)) and ask there? Hopefully someone else will have the answer. Good luck.

Well thank you for the help anyway :) I have asked with a thread at that site now :)

---

