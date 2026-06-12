---
title: "[SOLVED] Tv Out Problem Please"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by obscur156 on 2007-10-20
Hi everybody,i have an ati radeon x600.
I have just install the ati driver with envy,i have manage  making my tvout working for the first time.
Everything appear on my tv but the only thing that is not working is VIDEO like a movie or wathever.

I have tried every settings possible i think or i am missing one.
I have tried couple of different resolution and refresh rate but still no luck,movies just dont play on the tv.it stays black in the video player.
Using GUTSY.
Somebody have an idea?

Thanks ,best regards.

---

### Post by Blara on 2007-10-23
Same problem here, but with a radeon 9600 card. I had the same problem with feisty fawn but I sorted it out with some HOWTOs, now the problem is that I can find them (I don't remember what I did)

-EDIT-
*smack on forehead* just realized what it is.

edit your xorg.conf like so:
```

sudo gedit /etc/X11/xorg.conf

```

and find this section (or similar)
```

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AR [Radeon 9600]"
	Driver	"fglrx"
	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"
	BusID		"PCI:1:0:0"
EndSection

```

change the VideoOverlay to off, save the file and restart X (ctrl + alt + backspace or something) or reboot :D

---

### Post by realvz on 2007-10-23
what movie player are you using...
is it happening with multiple players...like totem, mplayer, vlc?
do yo have desktop effects enabled?

---

### Post by obscur156 on 2007-10-23
Thanks Blara i will try this tomorrow and will give feedback about it.

Realvz,its doing it in any media player,totem,vlc......
And my desktop effect are turned off.

I will try editing tomorrow so see ya.

Thanks for your reply,best regards.:)

---

### Post by obscur156 on 2007-10-24
Ok,i went to change my xorg.conf but the overlay was already OFF.
All the settings were like yours so its probably not that.

Thanks anyway budy,your help was appreciated.

I will wait for others to give more info on this.

Best regards.

---

### Post by obscur156 on 2007-10-26
Thank you  so much Blara :)

Since i have tried what you told me like i said in the previous post,my settings were already to OFF for the "OpenGLOverlay" "off".So it was not working...

This morning i tought to myself,why not trying the opposite.
So i have changed the setting for "OpenGLOverlay" "off" to "ON" saved the changes and restarted X.
(ctrl-alt-backspace)

After the restart of X,  BAAAMMMMMM i can see the video on my tv now.\\:D/\\:D/\\:D/\\:D/\\:D/.

Thanks again Blara even if it was a wrong answer or advice,you have pinpoint where was the problem.

So your THE MAN today Blara.

Best regards,have a nice weekend budy.:)

---

