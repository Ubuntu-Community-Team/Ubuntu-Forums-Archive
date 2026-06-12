---
title: "streaming .wmv from video sites"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by bmthFTW on 2008-02-20
hello all!
I am brand new to linux/ubuntu, total n00b, but i want to learn. My only problem at this point is simply watching videos embedded in webpages that use .wmv format. I simply get the video box as totally blank/black saying [no video]. Any help would be great! (btw, i have little/no experience with installing/downloading/anything with linux)

---

### Post by Presto123 on 2008-02-20
First up, get the Ubuntu Restricted Extras from Add/Remove (You may also need "GStreamer ffmpeg video plugin" also available in Add/Remove.). Second, if you feel that you will be watching Youtube or other flash videos, go to [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&ogn=EN_US-gntray_dl_getflashplayer](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&ogn=EN_US-gntray_dl_getflashplayer) and select the first one "tar.gz" and follow the instructions on that page.

---

### Post by spiderbatdad on 2008-02-20
Download the tar.gz here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
and follow the simple instructions just below the download options. That will get you some good experience installing things in Ubuntu. Or the flashplugin-nonfree is in synaptic, though it had issues not long ago...you should probably sudo -apt-get update...sudo apt-get upgrade before trying that one. also install ubuntu-restricted-extras from synaptic.

---

### Post by spiderbatdad on 2008-02-20
> **Presto123 said:**
> First up, get the Ubuntu Restricted Extras from Add/Remove. Second, if you feel that you will be watching Youtube or other flash videos, go to [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&ogn=EN_US-gntray_dl_getflashplayer](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&ogn=EN_US-gntray_dl_getflashplayer) and select the first one "tar.gz" and follow the instructions on that page.

:P

---

### Post by herbster on 2008-02-20
I don't think he's asking about Youtube (.flv) type files. I think what would help him is Mediaplayerconnectivity plugin, found here: [https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

bmthFTW, install that plug-in, restart Firefox and then go back to a page with some videos as you are mentioning. You should see a little icon/button in the middle of the black box now, click it and VLC/Xine/Totem will launch and stream your video.

---

### Post by Presto123 on 2008-02-20
> **herbster said:**
> I don't think he's asking about Youtube (.flv) type files. I think what would help him is Mediaplayerconnectivity plugin, found here: [https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

bmthFTW, install that plug-in, restart Firefox and then go back to a page with some videos as you are mentioning. You should see a little icon/button in the middle of the black box now, click it and VLC/Xine/Totem will launch and stream your video.

Yes, I know he's not asking...consider this a preemptive strike on a follow-up question. I didn't have to install that package you have mentioned, gstreamer plugins took care of it for me and covered offline .wmv videos as well.

---

