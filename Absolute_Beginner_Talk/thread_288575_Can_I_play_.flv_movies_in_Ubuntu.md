---
title: "Can I play .flv movies in Ubuntu?"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by Mimsy on 2006-10-30
A forum search came up blank. A Google search didn't take me very far either. Are there codecs or format converters available that make it possible for me to view my .fvl-movies under Ubuntu? 

Thanks,
Mimsy

---

### Post by andiii on 2006-10-30
I can play them with mplayer!

---

### Post by Mimsy on 2006-10-30
After some tinkering and downloading of plugins, I can now watch them just fine when I come to a website that has them embedded. My new problem is that when I download them, they sit on my desktop and call themselves silly things like "download_video.flv", and I can't play them with any of the Gnome applications.

/Mimsy

---

### Post by andiii on 2006-10-31
Have you tried mplayer?

---

### Post by Cynical on 2006-10-31
```
sudo apt-get install vlc
```

VLC can view flv files just fine.

---

### Post by Circus-Killer on 2006-10-31
as others have suggested try mplayer.

however i prefer converting .flv files into .ogg files. its quick, simple and painless.

simply install ffmpeg2theora
$ sudo apt-get install ffmpeg2theora

then to convert your .flv file just do the following:
$ ffmpeg2theora filename.flv

that will output to filename.ogg. if the audio/video is out of sync, retry with the sync option like follows:
$ ffmpeg2theora --sync filename.flv

easy, neh? ;)

---

### Post by andiii on 2006-10-31
Thats is a really good suggestion. Because even though mplayer could play .flv some things like forwarding etc didn't work.

Thanks

---

### Post by Mimsy on 2006-10-31
Yes! Converting, that's what I was looking for!

Thanks. I'll try it in a few days (*after* the evil term paper has failed to completly kill me - I hope), and if I have any problems, I'll be sure to let you know. :) 

/Mimsy

---

### Post by Mimsy on 2006-11-02
Here we go: I installed and tried it, and here's what happened:
> mimsy@Hawk:~$ ffmpeg2theora BallWorkOut.flv

File BallWorkOut.flv has unknown data format

I tried it with two other .flv files, to see if it was a one-time fluke.Same result. This puzzles me.

/Mimsy

---

### Post by Circus-Killer on 2006-11-02
you might wanna try [this]("https://help.ubuntu.com/community/RestrictedFormats") guide. just follow the easy-to-do instructions, and install what you want/need.

once you got all the codecs and plugins installed, you should be able to convert. thats the only thing i can suggest :-k . sorry.

---

### Post by Mimsy on 2006-11-02
That's odd; I followed that guide to set up formats when I did my last reinstall. I must have managed to mess it up since then.... I wonder if it would help to uninstall a bunch of things and then follow the guide from the beginning once again? I might have broken things when I was playing around with them. I do that a lot. :)

Thanks for your suggestions and help. I'll get this to work!

/Mimsy

---

### Post by grim4593 on 2006-11-05
Odd. I installed all the codecs on that guide and it still gives me this error when I try to convert:

[flv @ 0xb7f5ec30]Unsupported video codec (4)
... (many times)
[flv @ 0xb7f5ec30]Unsupported video codec (4)
[flv @ 0xb7f5ec30]Could not find codec parameters (Video: 0x0004)
Input #0, flv, from 'MVI_2872.flv':
  Duration: 00:00:45.3, bitrate: N/A
  Stream #0.0: Video: 0x0004, 15.00 fps(r)
  Stream #0.1: Audio: mp3, 11025 Hz, mono
      0:00:45.71 audio: 27kbps video: 0kbps    


It spits out an ogg but only has an audio component. If I play it with vlc or some other program it will either not display at all or only play the audio. I am confused.

---

### Post by Mimsy on 2006-11-06
The .flv movies I have still won't display in VLC or let me convert them with theora, however, when I tried them in mplayer it played the movies and the sound was just fine, so I'll just do that from now on. Thanks for your help, everyone! :)

/Mimsy

---

### Post by atomikpunx on 2006-11-13
[http://www.howforge.com/how-to-convert-flv-to-avi](http://www.howforge.com/how-to-convert-flv-to-avi)

> 
ffmpeg -i inputfile.flv -y outputfile.avi


if your a desktop whore like me, here is my exact file i just used.

> 
ffmpeg -i /home/nick/Desktop/input.flv -y /home/nick/Desktop/output.avi



note when you download the files they usually don't come with ".flv" and that throws alot of people for a loop because they type it, thinking its hidden, call it a old habit from winblows days. so rename it input.flv, and give this a shot.

---

### Post by Mohit on 2006-11-13
Try vlc player

code- sudo apt-get install vlc

or By going in the synaptic manager & select the Vlc player 

and install this
this will work
Mohit

---

### Post by Mimsy on 2006-11-13
Actually Mohit, if you look two posts above yours, you'll notice that VLC wasn't helping me at all. But thanks anyway.

Atomikpunx, thanks for the link and info! I'll save it for future use, since I'm sure it will come in handy. If nothing else, being reminded of the file path to my desktop is a good thing... :)

/Mimsy

---

### Post by grim4593 on 2006-11-16
Well I upgraded to flash9 beta and flv files work now. As a matter of fact they even appear with thumbnails!

---

