---
title: "How can i remove these?"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by Rackerz on 2005-11-16
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpe

That's the command i used to install the plugins. But the music doesn't really sound that good so im deciding to use RealPlayer. How can i remove the above plugins?

Thanks

---

### Post by Kyral on 2005-11-16
sudo apt-get remove gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg

---

### Post by canadianwriterman on 2005-11-16
They may also appear in Synaptic, so you could just open Synaptic and search for the gstreamer files. They should appear checked. Uncheck them and then apply. That'll remove them.

---

### Post by Rackerz on 2005-11-16
[QUOTE=Kyral]sudo apt-get remove gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg[/QUOTE]

I feel rather silly now, that was a bit obvious lol. 

Thankyou both for your help!

---

