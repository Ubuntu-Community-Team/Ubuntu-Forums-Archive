---
title: "Amarok woes"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Nekiruhs on 2007-05-21
Hi, normally, I think im pretty good with Linux, I've been using for about 6 months now and I've gotten the hang of it. I have heard many good things about Amarok, and am interested in using it. However, (this is really disgraceful) I cant figure out the interface. I cant even get a song to play! Please help, maybe a labeled screenshot is what I need. Also, I've heard that Amarok does not have native MP3 support, how do I add it, i can play mp3s in Rythmbox.

---

### Post by byenary on 2007-05-21
im not sure wich one but if you install every gstreamer package its gonna work...
I even think the 1.4 suggest wich package you need when trying to play mp3, he takes you into synaptic and do the nessecary...

---

### Post by adwatkin19 on 2007-05-21
My amarok worked by default with MP3's so im not too sure about that, but if you have issues i would suggest installing :

gstreamer plugins ugly multiverse

i installed that so i could rip using sound juicer to mp3

hope this helps

adwatkin19

---

### Post by bapoumba on 2007-05-21
@ Nekiruhs: I've deleted your duplicate thread.

---

### Post by Nekiruhs on 2007-05-21
Thanks, I managed to figure out how to atleast get a song to play, but now it says no Mp3 support. From looking on google there should be two buttons on a window that come up asking to add MP3 support. The window comes up, but the buttons dont.

---

### Post by koshari on 2007-05-21
you will need xine extra codecs

the latest amarok doesnt support gstreamer anymore.

---

### Post by Inxsible on 2007-05-21
I have Ubuntu Feisty installed and I tried a lot to get Amarok to work. When I  double clicked a song to play , it would give me the same window asking me to install mp3 support, I did install all the GStreamer plugins. Still no love !
 
After installation of the MP3 support , it would ask me to restart Amarok and then Amarok wouldnt start at all until I uninstalled and re-installed it again. I finally gave up and went with RhythmBox. Works great !
 
I had also tried getting Amarok from Medibuntu instead of the repos !! :(

---

### Post by Nekiruhs on 2007-05-21
> **Inxsible said:**
> I have Ubuntu Feisty installed and I tried a lot to get Amarok to work. When I  double clicked a song to play , it would give me the same window asking me to install mp3 support, I did install all the GStreamer plugins. Still no love !
 
After installation of the MP3 support , it would ask me to restart Amarok and then Amarok wouldnt start at all until I uninstalled and re-installed it again. I finally gave up and went with RhythmBox. Works great !
 
I had also tried getting Amarok from Medibuntu instead of the repos !! :(
I got MP3 working now type this in a terminal, then restart X (ctrl + alt + backspace)
```
sudo apt-get install libxine-extracodecs
```

---

### Post by koshari on 2007-05-21
and you dont need to restart the x server, just amarok.

---

### Post by Nekiruhs on 2007-05-21
Weird, i had to restart X, Amarok wouldn't come up after I installed.

---

### Post by Nekiruhs on 2007-05-21
Wow, now I've removed my menu bar and can't get it back. HELP!!

---

### Post by newportl on 2007-05-21
In Amarok?  Try Ctrl + M, that should bring your menubar back.

---

### Post by macbuzz on 2007-05-21
See Nekiruhs reply in this post.  I also got MP3 support working for Feisty through this method.  Not sure why Amarok didn't and go get MP3 support as it did with Edgy.  It's taken me nearly a month to stumble upon the right information so I can play MP3s.  I love Ubuntu but these are the kind of things that will keep it from being accepted by those with less persistence.

---

