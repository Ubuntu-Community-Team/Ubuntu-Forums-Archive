---
title: "[SOLVED] DVD's won't play"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by rmhodv on 2007-11-05
Hi 

I have installed Totem-xine and libdvdcss2, yet when I go to play a DVD I get the following message:-
[I][COLOR="Red"]
There is no plugin to handle this movie.
[/COLOR][/I]



In addition I also went to play a wmv file and go the following error message:-
[COLOR="Red"][I]
Video codec 'Windows Media Video 8' is not handled. You might need to install additional plugins to be able to play some types of movies[/I][/COLOR]

[COLOR="Black"]Any help would be great[/COLOR]

---

### Post by bump_ on 2007-11-05
Totem does that alot to me. Download vlc player. It plays many more types by default.


sudo apt-get install vlc

---

### Post by rsambuca on 2007-11-05
Try installing the [Restricted-Extras]("https://help.ubuntu.com/community/RestrictedFormats").

---

### Post by cotcot on 2007-11-05
Try 
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
```

---

### Post by rmhodv on 2007-11-05
> **bump_ said:**
> Totem does that alot to me. Download vlc player. It plays many more types by default.


sudo apt-get install vlc

Great.. It works. :) Thank you very much


* Just one thing though. How do you make VLC your defaut application?

---

### Post by Linuxratty on 2007-11-06
I popped in a DVD and get told i do not have permission to play the file!!! Then it tells me the plug in is not there even though I just installed it!
Vic also won't work.

---

### Post by rmhodv on 2007-11-07
> **Linuxratty said:**
> I popped in a DVD and get told i do not have permission to play the file!!! Then it tells me the plug in is not there even though I just installed it!
Vic also won't work.

Have you installed the libdvdcss2 file?

*If not you can download it from here [http://www.videolan.org/vlc/download-debian.html](http://www.videolan.org/vlc/download-debian.html)

---

### Post by magnus07 on 2007-11-08
I have installed all gstreamer plugins, libdvdread3 and used install-css.sh BUT says I don't have the codecs...
did all again but same result.
on another machine, I did the same and works.... :(
my version is 7.10 gutsy
thanks for any hint

---

