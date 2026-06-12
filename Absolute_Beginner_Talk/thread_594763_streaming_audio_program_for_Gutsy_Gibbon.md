---
title: "streaming audio program for Gutsy Gibbon?"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by KevNice on 2007-10-28
With Breezy Badger there was the Streamtuner player, and that was quite cool. I was hoping to install the same thing on Gutsy Gibbon but I can't find a program like this. Is there one? Any suggestions?

Also, how do I listen to streaming audio files that were built to run for Realplayer, WMP, etc?

Thanks guys

Kev

---

### Post by qamelian on 2007-10-28
Streamtuner is still in the Gutsy repos. For your other streaming needs, there is a linux version of Realplayer, or you could go the route of the mplayer plugin and w32codecs. Anything that you could do on your older release, you can still do on Gutsy, but much of it is a lot easier now. 

If you have a file type you want to play, play one locally first so it loads in Totem. Totem will try to detect the necessary codec and will offer to install it for you.

---

### Post by ghantoos on 2007-10-28
Try VLC (sudo apt-get install vlc), it's quite complete.

cheers,

ghantoos

---

### Post by Cochise on 2007-10-28
exaile will also stream i think

---

### Post by KevNice on 2007-10-28
Thanks guys, got the streamtuner up and going.

Tried to download and install RealPlayer 10, and after I did the chmod +x and tried to run the program, I got this message:

kevin@kevin-laptop:~/Desktop$ sudo ./RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

I also installed VLC, and while it streamed, I could not get any sound; not sure if its VLC or the file, thats why I want to install Realplayer as well so I can confirm.


Any advice?

---

### Post by linuxlizard on 2007-10-28
I've always used streamtuner myself, and you can get it easily from system- administration- synaptic.

But, I installed exaile last week and I'm not sure if I'll go back to streamtuner. It has a lot of sweet little plugins and tweaks in the setup menus and now when I'm listening to stations, I've got nice album art  showing up on my desktop to go with the song playing on the station, and I've got it so if I click close it shrinks to the dock. It's pretty sweet. Highly recommend trying it.

---

### Post by sailor2001 on 2007-10-28
I use xmms (synaptic) with streamtuner

---

### Post by KevNice on 2007-10-28
> **linuxlizard said:**
> I've always used streamtuner myself, and you can get it easily from system- administration- synaptic.

But, I installed exaile last week and I'm not sure if I'll go back to streamtuner. It has a lot of sweet little plugins and tweaks in the setup menus and now when I'm listening to stations, I've got nice album art  showing up on my desktop to go with the song playing on the station, and I've got it so if I click close it shrinks to the dock. It's pretty sweet. Highly recommend trying it.

Ok i got Exhaile, solved the problem of the streaming radio, I just put it into exhaile and it plays off of there.

Exhaile doesn't seem to come preloaded with any radio sites though, got any recommendations?

---

### Post by Wiebelhaus on 2007-10-28
> **ghantoos said:**
> Try VLC (sudo apt-get install vlc), it's quite complete.

cheers,

ghantoos

Just to reiterate.

---

### Post by linuxlizard on 2007-10-28
In exaile- go to edit, plugins and click the box next to shoutcast radio and desktop cover. A radio tab will appear to the left in exaile where you can access shoutcast, set your bookmarks, etc.

---

### Post by KevNice on 2007-10-30
right on, thanks. the names of the streams are different but its working!

Kev

---

### Post by andrew.46 on 2007-10-31
Hi,

 IMHO the ultimate streaming *anything* program for linux is mplayer but I will admit it is not as user friendly as some of the other programs suggested here:

[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

           Andrew

---

