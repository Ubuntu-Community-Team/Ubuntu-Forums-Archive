---
title: "CPU 99% might be related to sound?"
date: 2005-06-26
forum: Absolute Beginner Talk
---

### Post by thoffland on 2005-06-26
I have gkrellm installed because I kept getting error messages about my sound failing (I forget the exact message) it said that it would load a null sound something.... 

I played with the settings in the control panel and tried a few other things in my xorg.conf that I found in the forums but nothing helps. It resolves itself after I get the error message, but sometimes it takes 30min or more to pop up... until then I'm running at 99%cpu which lags. 

I have a generic sound card, but I just installed the drivers form my Nvidia GE FX 5500 video card, I think it was happening before that though... hard to tell. I've only been on linux for 3 days now... i'm a cherry!

---

### Post by monchichi on 2005-06-26
Run gnome-system-manager and see exactly what process it is that is eating up your CPU, then report back here.

---

### Post by poofyhairguy on 2005-06-26
[QUOTE=monchichi]Run gnome-system-manager and see exactly what process it is that is eating up your CPU, then report back here.[/QUOTE]
 

Please.

---

### Post by thoffland on 2005-06-27
The system monitor was the key, but I had to choose "running programs" in order to see it.. artsd was the culprit hogging up the cpu. So I ended the program, did a little research and installed gstreamer and that seemed to take care of it. Now i'm only using 21% as I type with xmms and SuperKaramba running. 

New problem came up though, I have no system sounds anymore... even at the loading screen I know it made some light sounds, and after I'm logged in there's nothing. XMMS works fine, but otherwise there no other sounds. I'm going to start searching for answers but if you know of a solution please feel free to post! 

Any ideas?

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=thoffland]
Any ideas?[/QUOTE]

I can help here. Read this first:

[http://www.ubuntuforums.org/showthread.php?t=26567&highlight=esd](http://www.ubuntuforums.org/showthread.php?t=26567&highlight=esd)

Then apply this thread if you need to:

[http://www.ubuntuforums.org/showthread.php?t=32063&highlight=esd](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=esd)

---

### Post by monchichi on 2005-06-27
[QUOTE=thoffland]Any ideas?[/QUOTE]
Wait.. you're using KDE? I don't think you can use ESD to play KDE system sounds. You might have to figure out what the problem is with artsd if you want the system sounds.

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=monchichi]Wait.. you're using KDE? I don't think you can use ESD to play KDE system sounds. You might have to figure out what the problem is with artsd if you want the system sounds.[/QUOTE]


ooooooops.

---

### Post by thoffland on 2005-06-27
Ya, I didn't realize it was a different animal...  the whole thing was working before I started tinkering with it too much... my fault entirely. 

I'm going to reformat/partition and install Kubuntu instead of the ubuntu with KDE addon and see if that makes things any better. 

Can I still come here for help? Or do I need to use the smaller kubuntu forum?

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=thoffland]Ya, I didn't realize it was a different animal...  the whole thing was working before I started tinkering with it too much... my fault entirely. 

I'm going to reformat/partition and install Kubuntu instead of the ubuntu with KDE addon and see if that makes things any better. 

Can I still come here for help? Or do I need to use the smaller kubuntu forum?[/QUOTE]


You can come here. Sure. I personally can't help as much, and you might like the kubuntu forums better.

---

### Post by thoffland on 2005-06-27
I'll be back! 

Thanks for your help, too bad I didn't explain myself better. It's been a good learning experience though, picked up some new commands and learned about a few new tools in Ubuntu that Iwouldn't have known of otherwise. 

What a great system!! I cant wait to drop Windows!

---

### Post by thoffland on 2005-06-28
[QUOTE=poofyhairguy]I can help here. Read this first:

[http://www.ubuntuforums.org/showthread.php?t=26567&highlight=esd](http://www.ubuntuforums.org/showthread.php?t=26567&highlight=esd)

Then apply this thread if you need to:

[http://www.ubuntuforums.org/showthread.php?t=32063&highlight=esd](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=esd)[/QUOTE]
 FYI: I reinstalled Ubuntu with Gnome and setup the sound per the tutorials and everything is working great!

---

