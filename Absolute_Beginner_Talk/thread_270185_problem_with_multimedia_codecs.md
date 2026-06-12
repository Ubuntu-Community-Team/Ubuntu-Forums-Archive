---
title: "problem with multimedia codecs"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by cmaranhao on 2006-10-02
i'm trying to install the codecs but this happens:

> maranhao@maranhao-desktop:~$ sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
> gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
> gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs
Reading package lists... Done
Building dependency tree... Done
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
[COLOR="Red"]E: Couldn't find package gstreamer0.10-plugins-bad-multiverse[/COLOR]
maranhao@maranhao-desktop:~$


what should i do?

---

### Post by meng on 2006-10-02
Do you have multiverse repositories enabled?

---

### Post by fatsheep on 2006-10-02
If you don't have the multiverse repositories enabled then go here:

[https://help.ubuntu.com/community/Repositories/Ubuntu#head-a86dddc6826cec4a3847d8441b24051d07b8dc64](https://help.ubuntu.com/community/Repositories/Ubuntu#head-a86dddc6826cec4a3847d8441b24051d07b8dc64)

---

### Post by cmaranhao on 2006-10-02
> maranhao@maranhao-desktop:~$ sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
> gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
> gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs
Password:
Reading package lists... Done
Building dependency tree... Done
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
[COLOR="Red"]Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate[/COLOR]
maranhao@maranhao-desktop:~$


still not working :???:

---

### Post by meng on 2006-10-02
Install everything else first (same command but omit w32codecs).
Then use wget to download the deb file for w32codecs from another site, and install using dpkg as described here:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by cmaranhao on 2006-10-02
it still doesn't work...

---

### Post by meng on 2006-10-02
Well hang on, I just don't understand that at all. What error message are you getting now? You posted error messages the first two times, that allowed us to identify your problem. Now you expect me to guess what's wrong?

---

### Post by cmaranhao on 2006-10-02
this time around it installed with no problems.. but when i try to open the files (for example a movie file ) with movie player it says:

An error occurred

yo do not have a decoder installed to handle this file.
you might need to install the necessary plugins

---

### Post by meng on 2006-10-02
Okay then - I thought your problem was completely different - what happens when you do this?
sudo apt-get install totem-gstreamer

---

### Post by cmaranhao on 2006-10-02
it works now :)

but now something odd is happening..

i tried to listen a mp3 file in amarok and it said:

"you will need the mp3 update" or something

i've done the update but now amarok won't open at all (it opened before the update)

---

### Post by meng on 2006-10-02
Sorry I don't know anything about amarok.

---

