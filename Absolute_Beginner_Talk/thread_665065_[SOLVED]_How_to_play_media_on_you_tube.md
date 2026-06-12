---
title: "[SOLVED] How to play media on you tube"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by tjwoosta on 2008-01-11
I just yesterday downloaded ubuntu and i know nothing about linux.
My problem is that i cannot play videos on youtube.
 When i first went to the site the bar at the top told me i need to install something to view this media. 
So i tried the first one on the list which i think was flash but it said i would have to pay for it so i ended up picking the bottom one which was gnash it downloaded and installed and i still cannot watch youtube. The bar that said i should install something doesn't show up anymore and the little circle in the youtube box just keeps spinning never connecting. I know my connection is fast enough because i have vista on another partition on my hardrive, there i can watch youtube fine.
Please if anyone can  help me i would appreciate it.

---

### Post by Hospadar on 2008-01-11
it's a little misleading, because although the license for flash disallows certain things, and is therefore considered non-free, it doesn't cost any money, so that's what you really want to install.

What you'll want to to, is go into System->Administration->Synaptic Package Manager and search for "gnash" you'll want to right-click and mark "gnash" and "mozilla-plugin-gnash" for uninstallation (also if there are other gnash packages installed gnash-common, gnash-cygnal or anything else with gnash in the name, uninstall those as well.

Then search again for flashplugin-nonfree and install that, then when you're all done, click apply to make the changes you marked.

That should do it for you, if not, try restarting your machine, and if it still doesn't work, then we'll talk manual installation (which is easy, but usually not needed)

---

### Post by PmDematagoda on 2008-01-11
Gnash is still in development and because of that you might be better off using Flash at least until Gnash has reached a good level of functionality.

Remove Gnash using:-
```
sudo apt-get remove gnash
```
and install Flash using:-
```
sudo apt-get install flashplugin-nonfree
```

You should then be able to view You Tube videos.

---

### Post by articpenguin on 2008-01-11
if is using gutsy apt-get install flashplugin-nonfree wont work. Its broken for somereason.

try install installing flash from here
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

---

### Post by nikoPSK on 2008-01-12
> **articpenguin said:**
> if is using gutsy apt-get install flashplugin-nonfree wont work. Its broken for somereason.

try install installing flash from here
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)


why are all the comments clashing? flash non-free should be jsut fine for you. gnash seems to fail for me. I am glad that adobe is supporting Linux for This.

nikoPSK

---

### Post by anderskitson on 2008-01-12
[SIZE="4"]To get flash working properly for you tube, your going to want to follow this tutorial
[http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)
Just follow the archived instructions, its really quite easy
 
The newest flash has bugs for Linux, it may say its installed but its not and gnash works on you tube but not very well, 

"Note: If you install the Adobe flash player plugin without viewing the detailed terminal text, the package will appear to be installed, but Flash will not work in Firefox "
 This is basically what most people think has happened. 
this fix works great for me.[/SIZE]

---

### Post by nikoPSK on 2008-01-12
> **anderskitson said:**
> [SIZE=4]To get flash working properly for you tube, your going to want to follow this tutorial
[http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)
Just follow the archived instructions, its really quite easy
 
The newest flash has bugs for Linux, it may say its installed but its not and gnash works on you tube but not very well, 

"Note: If you install the Adobe flash player plugin without viewing the detailed terminal text, the package will appear to be installed, but Flash will not work in Firefox "
 This is basically what most people think has happened. 
this fix works great for me.[/SIZE]

please don't put your text so big and bold. Also, non-free works for me... is there a current problem with it? :confused:

Best,
nikoPSK

---

### Post by tjwoosta on 2008-01-12
hey thanks guys  Youve been a great help i now have my youtube working like a charm.
Is there a way to mark this as solved?

---

### Post by nikoPSK on 2008-01-12
> **tjwoosta said:**
> hey thanks guys  Youve been a great help i now have my youtube working like a charm.
Is there a way to mark this as solved?

yes, top of the page, thread tools, mark this thread as solved. :)

---

