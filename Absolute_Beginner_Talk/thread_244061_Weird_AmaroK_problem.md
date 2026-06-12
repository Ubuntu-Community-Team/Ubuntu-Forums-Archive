---
title: "Weird AmaroK problem"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by slibuntu on 2006-08-25
Whenever i try to play tracks, mp3s, in amaroK, they dont play! It races through the list and then tells me playlist finished,its like its stuck on super fast forward! I'm baffled :confused: so any help would be appreciated!

---

### Post by Bachstelze on 2006-08-25
**gstreamer0.10-fluendo-mp3** package installed ? It's required to play MP3s in GStreamer app like amaroK.

---

### Post by slibuntu on 2006-08-25
Indeed, that package was not installed, however, installing it made no difference! Any other suggestions?

---

### Post by orb9220 on 2006-08-25
Use automatix or easy ebuntu to install all the codecs for audio and video then you don't have to worry about it anymore.

---

### Post by Bachstelze on 2006-08-25
Try installing **gstreamer0.10-plugins-bad** and **gstreamer0.10-plugins-ugly**, maybe you need something else that's in there.

---

### Post by ButteBlues on 2006-08-25
Settings > Configure Amarok... > Engine

Make sure you're using Gstreamer if you have installed the above pkg from the repos.

---

### Post by slibuntu on 2006-08-25
Still no change! The problem is,it looks like amaroK is playing the files, theres just no sound output, and the song progress bar jumps by minutes at a time. Pretty strange!

---

### Post by Bachstelze on 2006-08-25
Do MP3s work fine in Totem ?

---

### Post by slibuntu on 2006-08-25
No, nothing actually works in totem,totem is using the totem-gstreamer package, maybe try xine?  i just installed this a couple of weeks ago, but mp3s work fine in XMMS

---

### Post by Bachstelze on 2006-08-25
You could also try xine in amaroK (sudo apt-get install amarok-xine). But that's really weird, mp3s should play jut fine with the GStreamer plugins installed.

---

### Post by slibuntu on 2006-08-25
Actually i just noticed that other post about the gstreamer engine from a simple facade, it says xine in the settings and theres no gstreamer option
Also i'm a little automatix and easyubuntu-phobic, so id like to work it out myself

---

### Post by Bachstelze on 2006-08-25
So if you're using xine, you'll need the xine codecs :) Install the **libxine-extracodecs** package.

---

### Post by slibuntu on 2006-08-25
That did it! Thanks a million, now i can use "uncle rodney"s player of choice! Thank you for bearing with me!

---

### Post by msak007 on 2006-08-25
I use xine as an engine too instead of gstreamer, and have never had problems with the right codecs installed. I know you got the problem fixed, but just wanted to let you know that they've officially dropped the capital "K" at the end - it's now simply "Amarok" :)

---

### Post by crispy_420 on 2006-08-25
I've been searching for a simple solution like this thanks. Like someone before mentioned, I'm trying to avoid automatix and it's kin. THANKS!

---

