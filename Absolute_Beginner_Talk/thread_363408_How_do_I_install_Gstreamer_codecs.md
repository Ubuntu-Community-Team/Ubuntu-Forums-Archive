---
title: "How do I install Gstreamer codecs?"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by vmsolo on 2007-02-16
How do I use Synaptic Package Manager to install the Gstreamer codecs for mp3 support?
I don't have an internet connection on the PC running Ubuntu, but I downloaded them on another computer via the Ubuntu site, burned them on a cd and tried to get Synaptic PM to open and install them, but for some reason it refuses to see them.
Am I using the wrong codecs? The extension is ".deb".
Please let me know what's to be done about this; I really like Ubuntu, but I am completely ignorant to anything Linux.


Thanks in advance for any suggestions.

---

### Post by vmsolo on 2007-02-16
Btw, the version I am running is Edgy Eft.

---

### Post by MetalMusicAddict on 2007-02-16
If your on Edgy you can just double click on them to install them. Thing is, they have dependencies. Did you grab them as well?

---

### Post by vmsolo on 2007-02-16
well, it did work with gstreamer010-ffmpeg, but the "bad" and "ugly" ones give me an error message when I double click: "dependency is not satisfiable: libfaac0"
Maybe I have the wrong ones?

:confused: 

Did I grab them? (sorry, I'm really way below noob here....:oops:)

---

### Post by Maestro23 on 2007-02-16
[https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)

---

### Post by MetalMusicAddict on 2007-02-16
> **vmsolo said:**
> well, it did work with gstreamer010-ffmpeg, but the "bad" and "ugly" ones give me an error message when I double click: "dependency is not satisfiable: libfaac0"
Maybe I have the wrong ones?

:confused: 

Did I grab them? (sorry, I'm really way below noob here....:oops:)

No. You missed the dependency packages. It wont work. Is there any way you can get a internet connection?

---

### Post by vmsolo on 2007-02-16
> **Maestro23 said:**
> [https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)
thanks, but I did come across that page already, but it doesn't seem to mention the Edgy version of Ubuntu. Do the instructions for older versions work as well?
Is there a link to where I can download the proper version of the Gstreamer "bad" and "ugly" codecs for Ubuntu 6.10?

Please have patience with me. :(

---

### Post by vmsolo on 2007-02-16
> **MetalMusicAddict said:**
> No. You missed the dependency packages. It wont work. Is there any way you can get a internet connection?

Not right now. (no ethernet cable or wireless adapter :mad: )
Isn't there any way to download them separately (i.e. on my Mac, which I am using right now, and then copy them to the PC running Ubuntu via a CD)?

*hopeful*

---

### Post by 1001001 on 2007-02-16
This site provides you with information about all the packages available in the Ubuntu archive:

[http://packages.ubuntulinux.org/](http://packages.ubuntulinux.org/)

Just type the name of the file you need in the search box and make sure you select "edgy" in the distribution selection box.

---

### Post by vmsolo on 2007-02-16
Ok thanks.
I'll try downloading the codecs again.

---

### Post by vmsolo on 2007-02-16
I redownloaded all the the 'bad' and 'ugly' packages, but I still get an error when trying to install.
However, I did managed to install the one for DVD playback and 'ffmpeg' (which allows the Movie Player to play my divx files, but no sound...because it's missing the other ones I suspect).
I guess I'll have to give up for now, because I don't know what else to do.:( 
*sigh*

---

### Post by r4ik on 2007-02-17
Try,

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)

Don't forget "#How to add extra repositories"

Good luck !

---

### Post by vmsolo on 2007-02-17
Thanks, but I did manage to find a gstreamer mp3 plugin that actually works eventually (fluendo mp3 I think it's called)

---

