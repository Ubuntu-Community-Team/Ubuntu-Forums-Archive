---
title: "How do you listen to radio on the internet"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Charlie Dorff on 2007-11-06
Hi...
I was wondering if someone could explain how to listen to the radio on the insternet. I am using Ubuntu and I mostly listen to Minnesota Public Radio. I'll explain what I do and what the results are. I first go to [www.mpr.org](www.mpr.org). I click on the link that says listen. A dialog box appears that says "Open with Rhythmbox Media Player (default). I click ok and Rhythmbox Media Player opens but nothing happens. I've tried everything I could think of to get Rhythmbox Media Player to listen to MPR But nothing works. Could somone give me some pointers. Thanks.
Charlie

---

### Post by tgalati4 on 2007-11-07
>sudo apt-get install streamtuner
>streamtuner

At least you can listen to something else until you get it figured out.

---

### Post by kd7swh on 2007-11-07
Hey Charlie, 

I use VLC rather than Rhythmbox.
to install vlc copy this into the terminal:

```
sudo apt-get install vlc -y
```

this will install the vlc media player.  After it is installed open it from the sound and video menu or type ```
vlc
``` in the terminal.
in vlc you can click File -> Open Network Stream -> then select stream type (HTTP\MMS Most of the time)  and paste the stream URL into the box 
Click OK and your streaming

in the case of The Current mpr.org  stream the URL is: 

[http://minnesota.publicradio.org/tools/play/streams/the_current.pls](http://minnesota.publicradio.org/tools/play/streams/the_current.pls)


or you could just type ```
vlc http://minnesota.publicradio.org/tools/play/streams/the_current.pls
```

in the terminal 

if you don't like vlc try xmms.

enjoy

---

### Post by Charlie Dorff on 2007-11-10
Hi...
I'd like to thank the person who told me about VLC media player and how to install it. I can now listen to my favorite internet radio stations. I'd thank you by name but I did see your name on the reply. Thanks again.
Charlie

---

### Post by misfitpierce on 2007-11-10
lastfm player and lastfm.com

lastfm owns it all

---

### Post by Rinzwind on 2007-11-10
streamripper let's you save the stream too ;)

---

