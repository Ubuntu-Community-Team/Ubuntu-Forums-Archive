---
title: "Need help with embedded video in Firefox"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by Rich3077 on 2006-07-05
I have been trying for hours on end to make video files play embedded within Firefox. I have tried different how-to's and support threads from the Ubuntu forums and I just cant seem to make it work.  When I go to [http://trailers.apple.com/trailers/](http://trailers.apple.com/trailers/) I can see the video but its not embedded. I do have the mplayerconnectivity extension installed. Also when I tried to view a WMV file I got an error about codecs. I do have the restricted win32 codecs installed and am able to play DVD's with Totem. Mplayer has always given me problems. I can play DVD's with Totem but the same video will freeze with mplayer. Any help/tips/advice is appreciated.


Peace
Rich

---

### Post by Jagot on 2006-07-05
I followed the Restricted Formats guide and used the totem-xine-firefox-plugin and it works fine for me on the Apple Trailers site.  Are you sure you followed the guide correctly?

---

### Post by Rich3077 on 2006-07-05
[QUOTE=Jagot]I followed the Restricted Formats guide and used the totem-xine-firefox-plugin and it works fine for me o nthe Apple Trailers site.  Are you sure you followed the guide correctly?[/QUOTE]

I tried to follow the guide exactly... however there are some glitches like part of the process is to install a skin, but the link provided does not provide any skins, if you click on a skin you get a 404. Shouldnt matter becuase I already have a skin pack installed. There was also some other non-working links.. but I already had the stuff installed and even ran automatix again just to make sure.

I followed it to the best of my ability, copying and pasting comands to prevent typos. Still no luck.


Peace
Rich

---

### Post by Jagot on 2006-07-05
You are using this guide, right?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

There's nothing about skins on there.

---

### Post by Rich3077 on 2006-07-05
[QUOTE=Jagot]You are using this guide, right?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

There's nothing about skins on there.[/QUOTE]

Hmmm I was using this
[http://www.ubuntuforums.org/showthread.php?t=187709&highlight=embedded+wmv](http://www.ubuntuforums.org/showthread.php?t=187709&highlight=embedded+wmv)

---

### Post by Rich3077 on 2006-07-05
[QUOTE=Rich3077]Hmmm I was using this
[http://www.ubuntuforums.org/showthread.php?t=187709&highlight=embedded+wmv](http://www.ubuntuforums.org/showthread.php?t=187709&highlight=embedded+wmv)[/QUOTE]


As well as some other threads I found

---

### Post by Jagot on 2006-07-05
Well use the official Restricted Formats guide that I posted and all will be well.

---

### Post by Rich3077 on 2006-07-05
[QUOTE=Jagot]Well use the official Restricted Formats guide that I posted and all will be well.[/QUOTE]

I am checking it out now.. so far I havent found anything about embeded video in firefox, just the codecs that I already have.


Peace
Rich

---

### Post by Jagot on 2006-07-05
[QUOTE=Rich3077]I am checking it out now.. so far I havent found anything about embeded video in firefox, just the codecs that I already have.


Peace
Rich[/QUOTE]

[https://help.ubuntu.com/community/RestrictedFormats#head-e25afe1552d3a818f60e64143931b2d8e0522267](https://help.ubuntu.com/community/RestrictedFormats#head-e25afe1552d3a818f60e64143931b2d8e0522267)

---

### Post by nalmeth on 2006-07-05
A script like Easy Ubuntu or Automatix may be of use to you.

Try almighty automatix in my signature

Your probably looking for the mplayer-mozilla plugin, automatix will set that up for you no problem.

---

### Post by persev on 2006-09-13
> **nalmeth said:**
> A script like Easy Ubuntu or Automatix may be of use to you.

Try almighty automatix in my signature

Your probably looking for the mplayer-mozilla plugin, automatix will set that up for you no problem.
I have had trouble with this recently specifically my wife could not watch yahoo news videos. Here is how I fixed it.

Well I got it working! Took 3 days but finally success!  Okay here is what I did- first I removed w32codecs, mplayer, mozilla-mplayer, gstreamer0.10-pitfdll via synaptic; then I did "sudo apt-get remove automatix" in a terminal; then installed the latest version of Automatix; finally reinstalled codecs and Swiftfox browser with plugins. 
Now everything works in Swiftfox but if I open Firefox yahoo news videos still won't play in it.  I'm not sure which of these operations did the trick and I not going to undo everything to find out either as long as everything works under Swiftfox.

---

