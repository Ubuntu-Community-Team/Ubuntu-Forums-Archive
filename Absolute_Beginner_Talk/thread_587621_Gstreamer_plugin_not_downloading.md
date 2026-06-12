---
title: "Gstreamer plugin not downloading"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by tommy.sean on 2007-10-22
Can't play any media.
Totem movie player trys to play a DVD, MP3 or other music or video file and attempts to download a “Gstreamer” codec but every time I select the plugin from the list it fails, telling me “the list of applications is unavailable... click on reload to load it." (though there is only a  "refresh" button).
 I am sure there is an active internet connection and I know my sound card is setup  'cause ubuntu plays that catchy little jingle on startup.

Thanks.
noobie-tommy

---

### Post by Sef on 2007-10-22
There is a problem with GStreamer: Ugly.  It is missing a dependency, so it can't install.  I have some songs that I can't play without it being installed. sigh.

Try using synaptic, and see what error message it gives you and paste it here.

---

### Post by tommy.sean on 2007-10-23
Hrmm... I'm such a noob at Linux. 
How do I even find (or download and install) this  synaptic  program?

Thanks again.

---

### Post by zvacet on 2007-10-23
**system>administration>synaptic package manager**

---

### Post by tommy.sean on 2007-10-27
So Synaptic Package Manager shows seven gstreamer0.10 plugins listed and installed. I'm receiving no error messages and I don't see anything that looks like an error on the dependencies list. Should I try uninstalling and downloading and reinstalling the gstreamer plugins?

---

### Post by DezSP on 2007-10-27
First off, make sure you have "multiverse" selected in software sources (under Administration). Then run (in terminal):

sudo apt-get update
sudo apt-get install gstreamer0.10-plugins-ugly

And see what happens. ;)

---

### Post by tommy.sean on 2007-10-27
Well multiverse was not selected, so that helped and the   sudo apt-get update command said it worked but   sudo apt-get install gstreamer0.10-plugins-ugly gave me:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gstreamer0.10-plugins-ugly is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.10-plugins-ugly has no installation candidate

Thanks for the help

---

### Post by tommy.sean on 2007-10-27
Actually nothing on the list of "Downloadable from the Internet" in software sources. Can I select others?

---

### Post by DezSP on 2007-10-27
Eh, perhaps you're using Feisty or something? The package is called gstreamer0.10-plugins-ugly on my machine, but it might be slightly different on yours. Have a look on the list in Synaptic for something similar. I'd also recommend gstreamer0.10-ffmpeg if it's not already installed.

---

### Post by tommy.sean on 2007-10-27
Awesome! I can play mp3s and mpeg videos now. Thanks! I still can't play DVDs though and  Totem tells me I need a plug in fro DVDs but won't tell me how to get one. Is it also a gstream thing? :guitar:

---

### Post by tommy.sean on 2007-10-27
VLC player comes ready to play DVDs out of box (so to speak). Problem solved. Thanks for the help. Should I close this thread somhow?

---

### Post by zvacet on 2007-10-28
**Thread tools>mark this thread as solved**

---

