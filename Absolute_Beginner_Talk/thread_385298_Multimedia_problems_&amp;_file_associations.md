---
title: "Multimedia problems &amp; file associations"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by OriginalGrumpyOldMan on 2007-03-15
I have no luck whatsoever with the pre-installed multimedia players (Totem movie player, Rythmbox Music Player) Other than the pre-installed examples they are incapable of playing almost anything else, including MP3s???

VLC handles almost everything fine, but getting Ubuntu to use it as a default has been another prolonged challenge.

-- MP3s -over the network- (from a SMB share) ALWAYS open with Totem _Movie_ player, regardless of the default application selected in Properties / Open With. Actually it EVEN LISTS VLC as the default application! But when you double-click it, it still opens Totem Player instead?

Then, of course, Totem player fails with "You do not have a decoder installed to handle this file. You might need to install the necessary plugins." For an MP3 file?

-- So how about Rythmbox then: first, "Open With Other Application"/ Rythmbox Player will open Rythmbox, but the track will not be played. After you switch to the playlist view, then drag the MP3 on it, it would theoretically play it.

But instead: "Playback Error: The GStreamer plugins to decode "MP3" files cannot be found" Internet streaming ("Radio"): the 4 examples work, everything from SHOUTCAST DOES NOT: "Couldn't start Playback: Unknown playback error" or "You do not have a decoder installed to handle this file. You might need to install the necessary plugins." NB: I made sure they were MP3 streams.

-- The "good" news is that after I installed VLC, I was able to finally play back media files. But Ubuntu steadfastly refuses to set it as a default. I noticed that if I copy the MP3s to a LOCAL folder, the file association override works, and double-clicking will open VLC. But come on, I won't copy gigabytes of music from my server to the local drive just so they open in the correct app...

-- QUESTIONS:
- How do I change the default file association in Ubuntu, so that opening MP3s from the network will open in the preferred application?
- Is there an easy way to "fix" the built-in players to play back at least the more common formats?
- If not, How do I remove them? By default, Add/Remove will refuse, saying "Cannot remove: One or more applications depend on totem-gstreamer. To remove totem-gstreamer and the dependent applications, use the Synaptic package manager." Is that another app I need to install to un-install the obviously non-functional apps?

---

### Post by mikewhatever on 2007-03-15
You have to install restricted codecs to be able to use Totem and Rythmbox: [https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29)
VLC comes with the codecs, therefore works right away. To set it as default application for the type of file, right click on the file, choose properties, open with.

---

### Post by qiemem on 2007-03-15
This can be really frustrating when you first start using Ubuntu. mp3s and many other common formats are in fact proprietary formats and Ubuntu can't include them by default for legal reasons.

Luckily, it is very easy to install this stuff. To get it all at once, you can use this program called [EasyUbuntu]("http://easyubuntu.freecontrib.org/"). This will help you install the music and movie codecs, as well as some other handy stuff.

As far as changing the default program, I couldn't really tell ya. I've never run into the problem; when I try to open a media file, I usually open the program I won't to load it with first, and then navigate to the file via the programs "Open File" dialog. Or, right click on the file and select the program you want to open it with (i.e. on a movie file, Right Click->VLC). That should work well enough.

Good luck! Someone's bound to know how to change the actual default program, but this should hold you over till someone does.

Oh, one more thing. Installing the codecs (via EasyUbuntu or manually) will make music files work for all music players... No music player will play your mp3s w/o the codecs installed. So Rhythmbox should work fine after you run Easyubuntu.

---

### Post by kelbizzle on 2007-03-15
> How do I change the default file association in Ubuntu, so that opening MP3s from the network will open in the preferred application?
-Right click on the file
-hit p or click properties 
-click on the open with tab and change the default program

> - Is there an easy way to "fix" the built-in players to play back at least the more common formats?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

> If not, How do I remove them? By default, Add/Remove will refuse, saying "Cannot remove: One or more applications depend on totem-gstreamer. To remove totem-gstreamer and the dependent applications, use the Synaptic package manager." Is that another app I need to install to un-install the obviously non-functional apps?


```
sudo apt-get remove packagenametoberemoved
``` 
or ```
sudo apt-cache search packagenametomefound
``` to find it if you can't find the package

---

### Post by OriginalGrumpyOldMan on 2007-03-15
First: 
Thanks for all the pointers to set up the built-in players to handle those widespread (if proprietary) drivers!

As far as the file association goes, I would like to stress that I followed those steps, and indeed when playing local content, it works.
HOWEVER, it seems that for networked content, or perhaps content where Ubuntu can't change the properties(?) it will have a "fallback" which is Totem Player REGARDLESS of the actual app you have set in the "Open with" property
(It will go as far as list it as the default when you LOOK at the properties, but still USE Totem player instead)

---

### Post by kelbizzle on 2007-03-15
How do you browse the shares on the network to play your files? Maybe you have to mount your network shares (if their windows shares) using smbfs. It's what I use  Because when the share is mounted it looks like removable media.

---

### Post by melat0nin on 2008-03-15
Apologies for resurrecting an old thread, but I'm having the same problem.

I have a landisk which I can browse easily enough, but opening an AVI (divx) opens in Totem despite the default setting being VLC.

Any thoughts? As far as I can tell the shares on the landisk are mounted (if i right-click them in the Network Browser I have the Unmount option).

---

### Post by Mikaa on 2008-04-14
Same problem here.

When I installed VLC for first time (a few hours ago) and tested it over network (to windows share) it worked fine. Now it doesn't open them even not with right click open with... already set .avi player default VLC. It still opens up Totem even after reboot. Even after removing Totem with apt-get remove totem.

All in all problem not solved

---

### Post by k66473 on 2008-04-17
> **kelbizzle said:**
> -Right click on the file
-hit p or click properties 
-click on the open with tab and change the default program
...
this works fine with me.
thanks

---

