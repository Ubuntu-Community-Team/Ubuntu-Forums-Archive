---
title: "[SOLVED] Enable Flash in Opera"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2008-03-10
I have tried to follow the threads explaining how to do this but I am way too dumb to do it all by my lonesome. I have grown addicted to the joys of having someone tell me what to code and having me post results. Seriously, I need help.

---

### Post by scragar on 2008-03-10
strange... I'm using opera, and all I did was install the plugin using:
```
sudo apt-get install flashplugin-nonfree
```

but then I did restore my settings from a previous install, so that may have affected it...

---

### Post by boriquajake on 2008-03-10
> **scragar said:**
> strange... I'm using opera, and all I did was install the plugin using:
```
sudo apt-get install flashplugin-nonfree
```

but then I did restore my settings from a previous install, so that may have affected it...

You are right, from what I can tell, flash is installed it is just not working. I can't tell if it is installed in one place and being looked for in another or if it is somehow not properly enabled or what. I suspect it is something simple but I really don't know.

---

### Post by scragar on 2008-03-10
I checked my settings, and opera has flash down as:

```
/usr/lib/opera/plugins:/usr/lib/mozilla/plugins:/home/**scragar**/.mozilla/plugins:/usr/lib/firefox/plugins
```now, scragar is my username, so I'd assume yours would go in there (tools > preferences > advanced > content > plugin options )

sounds strange that it's leeching the plugin from firefox though


try this line:
```
sudo ln /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/lib/opera/plugins/
```
then restart opera(provided the line works ofcourse), see if flash works then. If that line doesn't work you can always boot up firefox(so it links to the plugin), then steal firefox's copy:```
sudo ln ~/.mozilla/plugins/libflashplayer.so /usr/lib/opera/plugins/
```

---

### Post by gi2k15 on 2008-03-10
I read in the Opera's help files that the most recent Flash Player plugin (9 update 3) is not working on the current Opera stable version for Linux, but it'll work on further versions. It's already working in the beta.

---

### Post by boriquajake on 2008-03-11
> **scragar said:**
> I checked my settings, and opera has flash down as:

```
/usr/lib/opera/plugins:/usr/lib/mozilla/plugins:/home/**scragar**/.mozilla/plugins:/usr/lib/firefox/plugins
```now, scragar is my username, so I'd assume yours would go in there (tools > preferences > advanced > content > plugin options )

sounds strange that it's leeching the plugin from firefox though


try this line:
```
sudo ln /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/lib/opera/plugins/
```
then restart opera(provided the line works ofcourse), see if flash works then. If that line doesn't work you can always boot up firefox(so it links to the plugin), then steal firefox's copy:```
sudo ln ~/.mozilla/plugins/libflashplayer.so /usr/lib/opera/plugins/
```

Brother Man, first of all, thanks for the help. Now, I pasted this into terminal:
> /usr/lib/opera/plugins:/usr/lib/mozilla/plugins:/home/jake/.mozilla/plugins:/usr/lib/firefox/plugins

and I got this:

> bash: /usr/lib/opera/plugins:/usr/lib/mozilla/plugins:/home/jake/.mozilla/plugins:/usr/lib/firefox/plugins: No such file or directory

What does that mean? Are my flash plugins stored somewhere weird.

---

### Post by forrestcupp on 2008-03-11
Here's what you need to do to get it working easily.

Open up Synaptic and go to Settings->Repositories.  Click the Updates tab in that window.  Check the boxes that say 'Proposed updates' and 'Unsupported updates.'  Then exit your repositories window and click the Reload button.  Then you will be able to install a newer flashplugin-nonfree that will automatically work in Opera without you having to do anything.

---

### Post by Arkenzor on 2008-03-11
Actually, the real deal is that Adobe manage to break Opera (and Konqueror) compatibility with its last flash player release. I'll guess scragar is using an older version of the plugin.

At any rate, the current Opera 9.50 beta fixed this and works just fine. It may be in the backports or unsupported repository (sorry, I can't check since I use another distribution these days), if not then you can get the package [here](http://www.opera.com/download/index.dml?platform=linux&ver=9.50b).


EDIT: Ah, didn't see someone posting before me...

---

### Post by boriquajake on 2008-03-11
> **forrestcupp said:**
> Here's what you need to do to get it working easily.

Open up Synaptic and go to Settings->Repositories.  Click the Updates tab in that window.  Check the boxes that say 'Proposed updates' and 'Unsupported updates.'  Then exit your repositories window and click the Reload button.  Then you will be able to install a newer flashplugin-nonfree that will automatically work in Opera without you having to do anything.

What you are saying makes perfect sense, but I have had those repositories enabled forever. What is really weird is that as far as I can tell the version of Opera I installed (the one that is in add/remove) seems to have flash already installed. I think this because when I open Opera and go to Tools->Advanced->Plug-ins, this comes up:

> Plug-ins
Shockwave Flashapplication/futuresplash	spl
application/x-shockwave-flash	swf
/usr/lib/flashplugin-nonfree/libflashplayer.so

NS4PluginProxyapplication/x-opera-nsplugin	-
/usr/lib/opera/plugins/libnpp.so

QuickTime Plug-in 7.2.0video/mp4	mp4
video/quicktime	qt,mov
image/x-macpaint	pntg
image/x-quicktime	pict, pict1, pict2
video/x-m4v	m4v
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so

Shockwave Flashapplication/futuresplash	spl
application/x-shockwave-flash	swf
/usr/lib/mozilla/plugins/flashplugin-alternative.so

Totem Web Browser Plugin 2.20.0audio/wav	wav
audio/x-wav	wav
video/mpeg	mpeg,mpg,mpe,m2v,m1v,mpa
audio/mpeg	mp3,mp2,mpga
application/ogg	ogg
audio/ogg	ogg
audio/x-ogg	ogg
video/ogg	ogg
video/x-ogg	ogg
application/x-nsv-vp3-mp3	nsv
video/flv	flv
/usr/lib/mozilla/plugins/libtotem-basic-plugin.so

DivXÂ® Web Playervideo/divx	divx
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so

Windows Media Player Plug-in 10 (compatible; Totem)video/x-msvideo	avi
video/x-ms-asf	asf,asx
application/asx	-
video/x-ms-asf-plugin	-
application/x-mplayer2	-
video/x-ms-wm	wm
video/x-ms-wvx	wvx
video/x-ms-wmv	wmv
video/x-wmv	wmv
application/x-ms-wms	wms
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so

Yet when I try to access a webpage with flash content (like the Adobe test page, for instance) I get bupkis. I am dying here!

---

### Post by Arkenzor on 2008-03-11
Have you tried using the Opera 9.50 beta as I suggested in my previous post?

---

### Post by boriquajake on 2008-03-11
> **Arkenzor said:**
> Have you tried using the Opera 9.50 beta as I suggested in my previous post?

No, I guess I sort of missed that one. I just looked for it in synaptic but I didn't see it. How do I get it?

---

### Post by boriquajake on 2008-03-11
> **boriquajake said:**
> No, I guess I sort of missed that one. I just looked for it in synaptic but I didn't see it. How do I get it?

Never mind, I am retarded. I just googled it and there it was. By the way, that was like the first time I have ever downloaded a linux app from somewhere other than synaptic and had it just install and work. Why is that so rare?

Anyway, thanks to everyone. I am now attending the Opera and seeing flash and all that crap.

---

### Post by Arkenzor on 2008-03-11
> **boriquajake said:**
> By the way, that was like the first time I have ever downloaded a linux app from somewhere other than synaptic and had it just install and work. Why is that so rare?

My experience is that it usually works as long as you can get a .deb package. I think...

---

### Post by boriquajake on 2008-03-11
> **Arkenzor said:**
> My experience is that it usually works as long as you can get a .deb package. I think...


Dude, I know you are right, it is just that I am way less technically savvy than most linux users. Normally I download a program and it shows up as some kind of a compressed archive, right? Anyway, the first thing I usually do is extract it and look for something that looks like it should trigger an install. I have even read all of the instructions telling me to look for the .deb files but what they don't say is how to find them. The downloaded programs don't have files called "Hey, this is the.deb file!!". I usually end up double clicking on things more or less at random and them closest I get to success is a window coming up asking me if I want to just run  or run in terminal but it doesn't matter which one I choose because nothing happens either way. Oh well. 

Anyway, thanks again for the help.

---

