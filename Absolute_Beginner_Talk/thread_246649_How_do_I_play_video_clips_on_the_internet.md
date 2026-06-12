---
title: "How do I play video clips on the internet?"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by Handssolow on 2006-08-29
I not getting very far playing video clips from the internet.

I have Totem Movie Player and Real Player 10.

If I go to the the Real Player site and select a test clip to play, a window opens asking me what Firefox wants to do with the clip, Totem Movie Player is the Default, not the option I'm wanting of Real Player 10.

OK I'm going instead to accept the Totem Movie Player (Default). If I then accept this, I get the following warning message-

      Totem could not play 'rtsp://media.real.com
      showcase/service/samples/realvideo10_ISDN.rm'.


      Internal GStreamer error: negotiation problem. 
      Please file a bug at [http://bugzil](http://bugzil)[/I]la.gnome.org/
      enter_bug.cgi?product=GStreamer[/I] .


So after looking for advice on this Forum and I,m thinking that  I need to do install the totem-gsteamer-firefox-plugin.

I go into Synaptic and select this plugin and get the following message-

      totem-gstreamer-firefox-plugin:
      Depends: totem-gstreamer (=1.4.1-0ubuntu4) but 1.4.3-0ubuntu1 
      is to be installed

My alternative plan to show video clips was to get Real Player 10 to be the default player. The Forum advice I found suggested using File Manager to change the properties of Real Player 10 but I didn't find anything that seemed appropriate.

So two questions for now.

What's my problem with the Totem firefox plugin? 

How do I alter the video player default,from Totem to Real Player 10?

---

### Post by PPAAUULL on 2006-08-29
You should take a look at this: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
It has instructions on how to get it working. I used it and it worked for me. Hope this helps.

Paul

---

### Post by Handssolow on 2006-08-29
Thanks.

Well I've made some progress. I can play video off the internet with Totem Media Player and I can now also play DVD discs.

I'm not sure of all things I've done in the past couple of hours to gets things working. I wasn't able to install the Totem-gstreamer-firefox plugin at first.

These places helped.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

[http://ubuntuforums.org/showthread.php?t=186792](http://ubuntuforums.org/showthread.php?t=186792)

I tried an earlier version of Totem MP and that didn't help so I reinstalled the latest version back.

I then got side tracked into testing my PC's ability to play DVDs and discovered I couldn't. I also discovered that if Synaptic was open, I couldn't load the suggested plugins. With Synaptic closed, I was then able to use the terminal to install these and then play DVDs for the first time.


Returning to the problem of playing video clips from internet, following advice from Ubuntu_Demon I installed code with the terminal and Synaptic closed, I could then load the Totem gstreamer firefox plugin and I was then able to play my first video clip.

I still need to get RealPlayer 10 to work.

---

### Post by Omnios on 2006-08-29
try geting the Media Player Conectivity extension for firefox. Its a bit ugy but seems to work

---

### Post by Handssolow on 2006-08-31
I've just got Real Player 10 to play test clips from Real's website. I'm posting this reply in case others have a similar problem.

I booted up the PC and there was an update for the Real Player.
"About" reports that I'm now running Real Player 10.0.8.805 (gold).

Initially when attempting to play the clip, Totem was offered as my default media player but I navigated to Real's via File System>usr>bin>Realplay and video appeared  :-)

---

### Post by Handssolow on 2006-09-02
Well, I discovered today that I wasn't able to play wmv video clips from a site on the internet.

I had Totem Movie Player with gstreamer which only played the sound, MPlayer played the sound but the video was only in black and white, RealPlayer didn't work, yet I seemed to have followed the appropriate instructions and codecs.

So following others' experiences, I decided to install Automatix.

Once installed, despite some reservations during the process when moving from gstreamer to xine things worked, I can now play wmv clips with Totem MPlayer-xine..

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

