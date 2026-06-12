---
title: "URGENT! Make VLC Default Player in Firefox"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-06-26
Hi, as some of you may know Wimbledon is happening right now in London and I have a paid subscription so that I can watch it online via a danish television vod service. The thing is they state on their website that on linux machine you need to have VLC player installed to use their service. Right now Totem is the embedded player in firefox, and it wont play the video.

SO i need VLC to be embedded in firefox and handle the video streams. I used to have this in windows but I canøt figure out how to do it in Ubuntu.

For information purpose, when i right click on the blank Totem canvas in firefox, I can copy the following link:
mms://mms-vod.media.tele.dk/tv2vod/vod/568720.wmv?handle=24718726:61af82adc0fcf4651c9ae4554e1892e5

How would I go about embedding vlc in firefox I'm not interested in opening a separate windows and pasting the url I want it embedded if possible

---

### Post by speaker219 on 2007-06-26
remove any totem plugins you have installed in mozilla
sudo-apt get remove totem-mozilla
then, download and install the "Media Player Connectivity" add-on for Firefox
[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

Then, make sure you configure your settings for "Windows Media" videos to play with vlc (/usr/bin/vlc)
then, when you go to view your VOD videos, click the play button and it should play with VLC.
enjoy!

---

### Post by Lord Illidan on 2007-06-26
```
sudo apt-get install vlc-plugin-alsa
``` appears to do the trick.

---

### Post by Lord Illidan on 2007-06-26
> **speaker219 said:**
> remove any totem plugins you have installed in mozilla
sudo-apt get remove totem-mozilla
then, download and install the "Media Player Connectivity" add-on for Firefox
[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

Then, make sure you configure your settings for "Windows Media" videos to play with vlc (/usr/bin/vlc)
then, when you go to view your VOD videos, click the play button and it should play with VLC.
enjoy!

Nice one!

But the command is this : ```
sudo apt-get remove totem-mozilla
```

---

### Post by kasperbs on 2007-06-26
Hi I tried both of the methods but nothing seems to work for me. I even tried to launch the stream in an external vlc player but nothing helped, I tried with different streams also free ones as I thought it might have been the stream that was the problem.

But the stream listed underneath here should be a free stream so could anyone try it out for me and see if it will play in VLC. It wont play in mine!

> mms://mms-vod.media.tele.dk/tv2vod/vod/569618.wmv?handle=24747572:20889b2a54f8872cfb0015145bd735ea

thanks

---

### Post by speaker219 on 2007-06-26
> **Lord Illidan said:**
> Nice one!

But the command is this : ```
sudo apt-get remove totem-mozilla
```

Ah! Woops, typo =)

---

### Post by speaker219 on 2007-06-26
Try installing the w32codecs package:
```
sudo apt-get install w32codecs
```

---

### Post by kasperbs on 2007-06-27
I already have those codecs installed! Have you tried the link in your VLC player?

---

### Post by speaker219 on 2007-06-27
kasberbs, i did try it in vlc, and it appears like its playing a live stream because the timer is still up but it stays at "0:00:00/0:00:00" i've never seen that before, i don't know what the problem could be. have you tried mplayer?

---

### Post by paradoxni on 2007-06-27
vlc not working for that stream you posted either.. mplayer completely froze..but my router lights flashed as if it was trying to connect at least.

as for the urgency..dont worry I have Wimbledon here on the BBC and its a washout with rain so your not missing any tennis :)

---

### Post by kasperbs on 2007-06-27
Well thanks for trying anyway, I guess I have to find a way to get hold of a windows copy and get it running IE and WMPlayer.... SIGH :(

And as long as it's raining I should have the time to find a windows cd :)

---

### Post by gn2 on 2007-06-27
Have you tried installing VLC Media Player through Automatix, along with the various non-free and DVD Codecs that are available there?
.
May be worth a try before installing Windows again?
.
[www.getautomatix.com](www.getautomatix.com)

---

### Post by Inxsible on 2007-06-27
If the plugin thing doesnt work for you. you can actually use the application to run the video.

Edit -- > Preferences. Contents tab. Under the File Types heading, click Manage.

Change the action for the file type you want to see, and instead of using the plugin, you can choose to download the video or select an application to view the video in :)

Hope that helps !!

---

### Post by rocknrolf77 on 2007-06-27
Have you tried mplayer + ffmpeg ?

---

### Post by kasperbs on 2007-07-02
> Have you tried mplayer + ffmpeg ?
What doies that mean and how do I do it?

---

### Post by garlicsalt2 on 2007-07-03
Okay, I came to UbuntuForums to see if anyone had a solution, but I didn't find one. After trying SOOOOOO many things, I finally did a Google search for
>  firefox mms associate 
and found the following site: []http://chim0.blogspot.com/2006/04/associate-mms-links-with-mplayer-in.html](]http://chim0.blogspot.com/2006/04/associate-mms-links-with-mplayer-in.html)

This works for me now, just wonderfully, although I substituted the command ```
/usr/X11R6/bin/vlc
``` instead of using mplayer, like is mentioned in the instructions.

That's it! No extra Firefox plugins, add-ons, or extensions needed. I do have w32codecs installed from the Medibuntu ([http://medibuntu.sos-sts.com/"](http://medibuntu.sos-sts.com/")) repository. I also have most of the gstreamer0.10 packages, as well as, sox, alsa, ffmpeg, etc.

---

