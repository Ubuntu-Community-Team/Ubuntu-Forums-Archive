---
title: "mp3s won't play"
date: 2005-09-06
forum: Absolute Beginner Talk
---

### Post by thepcdoctor on 2005-09-06
I've installed multimedia codecs as per ubuntu guide but mp3's still don't play.
Totem tells me there were no decoders and music player couldn't parse list. What do I do now?

---

### Post by davmac on 2005-09-06
Have you tried playing them with XMMS or RhythmBox? Any joy with these?

---

### Post by Kvark on 2005-09-06
Totem is worthless without the package called totem-xine so thats prolly what you need.

---

### Post by KingBahamut on 2005-09-06
[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

Be sure you have the backports repositories, then install and register the proper codecs. 

Dont bother using Totem for media anything. I dont know about everyone else, but I find it almost absolutely worthless. 

probably want to use something like rhythmbox or xmms.

---

### Post by thepcdoctor on 2005-09-06
Done the backports and codecs thing as per guide. How do I register the codecs?

Would that be apt-get rhythmBox install?

I've installed xmms...but no sound??

---

### Post by thepcdoctor on 2005-09-06
ok...figured out sound problem.

---

### Post by KingBahamut on 2005-09-06
Lol....thats what we are here for pcdoc.

---

### Post by thepcdoctor on 2005-09-06
where is rhythmbox to be found?  XMMS is a poor man's winamp.

---

### Post by KingBahamut on 2005-09-06
[QUOTE=thepcdoctor]where is rhythmbox to be found?  XMMS is a poor man's winamp.[/QUOTE]
 Rhythmbox should be on your system by default I think. 

I think they put it in the sound/video directory as Music Player or something. 

or just run application -> rhythmbox

---

### Post by gireluh on 2005-09-06
I have a similar problem, I've just installed hoary and I'm looking a way to play my mp3 but I just can't find some help on installing the codecs WITHOUT INTERNET

I don't have an internet connection at home, so please could someone give me a site where I can manually download the codecs I need so then I can install them using synaptic and a local folder?

please help a noobie transfer to ubuntu

---

### Post by cnayak on 2005-09-06
[QUOTE=gireluh]I have a similar problem, I've just installed hoary and I'm looking a way to play my mp3 but I just can't find some help on installing the codecs WITHOUT INTERNET

I don't have an internet connection at home, so please could someone give me a site where I can manually download the codecs I need so then I can install them using synaptic and a local folder?

please help a noobie transfer to ubuntu[/QUOTE]

 try searchig for xmms-mp3 plugin on the net. If you don't have xmms installed, then get the tarball  ( that probably has the mp3 plugin enabled) and compile it ( I assume you have the required libraries)

---

### Post by Wolki on 2005-09-06
[QUOTE=thepcdoctor]where is rhythmbox to be found?  XMMS is a poor man's winamp.[/QUOTE]

Well, there are a lot of other music players you can try. beep-media-player (bmp) is a richer man's winamp. Rhythmbox is a media player that many consider to have an itunes-like interface (don't know about that, never used itunes). amaroK is a power-tool that has nearly endless features (I find it a bit overcomplicated, but there are lots who swear by this player. It'll need kde libs but runs fine under gnome). Totem  is fine for playing a quick file. Quod libet is another media player that some people use.

And then there's my personal favorite, Muine. It's a library-based player with a really simple, quick interface that keeps features and options really low, but is extensible with plugins.

> I don't have an internet connection at home, so please could someone give me a site where I can manually download the codecs I need so then I can install them using synaptic and a local folder?


Try the Ubuntu addon cd if you have access to a cd burner:  [http://ubuntuforums.org/showthread.php?t=30147](http://ubuntuforums.org/showthread.php?t=30147) 

I didn't use it since i have broadband, but i guess it will improve your Ubuntu experience a lot.

---

### Post by thepcdoctor on 2005-09-07
Rhythm box doesn't parse mp3's, so don't know what that's all about.  I might check out the richer man's winamp as you suggest.  Is getting the codecs for this straightfoward?

---

### Post by Vulpus on 2005-09-07
[QUOTE=Wolki] amaroK is a power-tool that has nearly endless features (I find it a bit overcomplicated, but there are lots who swear by this player. It'll need kde libs but runs fine under gnome). Totem  QUOTE]

I am one of those who swear by amaroK, tis brill!

---

### Post by Kvark on 2005-09-07
[QUOTE=thepcdoctor]Rhythm box doesn't parse mp3's, so don't know what that's all about.  I might check out the richer man's winamp as you suggest.  Is getting the codecs for this straightfoward?[/QUOTE]
[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

---

### Post by doclivingston on 2005-09-07
[QUOTE=thepcdoctor]Rhythm box doesn't parse mp3's, so don't know what that's all about.  I might check out the richer man's winamp as you suggest.  Is getting the codecs for this straightfoward?[/QUOTE]

As people have said, check out [http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs). In particular the package you need for mp3 playback in totem/rhythmbox is "gstreamer0.8-mad"

---

### Post by thepcdoctor on 2005-09-08
As I said earlier I installed the codecs as per guide but clicking on Rhythm box I get the can't parse message. Have I missed an important step?  It seems you often need to do X before you do Y before you can do Z in Linux.  I'm still learning...

---

### Post by doclivingston on 2005-09-08
Can you open up a terminal and run "gst-inspect mad"? If it is installed properly, that command should print out a heap of info. If it prints out "No such element or plugin 'mad'", can you run "sudo gst-register" and try "gst-inspect mad" again?

* If the first gst-inspect prints out a heap of info, but Totem and Rhythmbox refuse to play mp3s, something odd is going on.
* If the first gst-inspect says that there isn't an element or plugin, but it works after running gst-register, then for some reason gst-register didn't get run automatically when you installed the gstreamer plugin package (it *should* get run automatically)
* If gst-inspect still says that the plugin doesn't exist, even after running gst-register, then the gstreamer-mad package isn't installed correctly.

---

### Post by Wolki on 2005-09-08
[QUOTE=Vulpus]I am one of those who swear by amaroK, tis brill![/QUOTE]

Maybe. I somehow don't understand it and always get lost in its myriad of views, options, settings etc when I just want to play a few songs ^^;;

I'll try it again sometime, if I find the time and concentration.

---

### Post by thepcdoctor on 2005-09-09
theboss@ubuntu:~$ gst-inspect mad
bash: gst-inspect: command not found
theboss@ubuntu:~$ run gst-inspect mad
bash: run: command not found

What now?

---

### Post by doclivingston on 2005-09-10
[QUOTE=thepcdoctor]theboss@ubuntu:~$ gst-inspect mad
bash: gst-inspect: command not found
theboss@ubuntu:~$ run gst-inspect mad
bash: run: command not found[/QUOTE]

Now that I think about it, the package "gstreamer0.8-tools" might not be installed by default - and you need it installed to run the commands I had above. Alternatively you may have to append "-0.8" to the commands, but I think you shouldn't have to do this on hoary.

---

