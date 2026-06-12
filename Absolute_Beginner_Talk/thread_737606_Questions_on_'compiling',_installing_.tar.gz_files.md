---
title: "Questions on 'compiling', installing .tar.gz files, and gtkpod"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Horomancer on 2008-03-27
Hey There! I've been having trouble using gtkpod to sync music to my iPod (the new Nano).
After doing a little research i found that
1) The current version of gtkpod installed on my system is 0.99.10 and i got it form the gtkpod-acc file in Synaptic
2) the current libgpod file is version 0.5.2-2, also found through Synaptic
3) the current gtkpod version is 0.99.12, found from the gtkpod website and
4) the latest build of gtkpod relies on libgpod version 0.6.0

I downloaded and saved the file libgpod-0.6.0.tar.gz from source forge.

If i'm not mistaken i now open a terminal and go to the directory that the .tar.gz file is saved with the 'cd' command then type in 'config' and 'make' to install the libgpod file.
But what will that do? will that alter my gtkpod program? after i config and make will i be able to click on gtkpod and it will now be 0.99.12? do i need to download and reinstall gtkpod from thier website? is there anyway to do all this from the GUI? And why are the latest versions not in the repositories so i can use Synaptic?
I know i installed tomboy notes v0.10 from an ubuntu website (getdev i think it was called). Is there anything like that for the latest build of gtkpod?
Thank you for helping this noob

---

### Post by twright on 2008-03-27
no need to compile anything, just install the latest version from the hardy repos (see link in my sig)

---

### Post by cisforcojo on 2008-03-28
I strongly recommend you use Floola instead of GTKPod. It's a much better app imo.
[http://www.floola.com](http://www.floola.com)

---

### Post by Horomancer on 2008-03-28
Thank you twright, that walk through did the trick.
I got an error message though about gtkpod not being able to edit the image folder or something of that nature. Also when i tried to load up one of my audio books (in the Audibles's .aa format) gtkpod gave me an error saying it did not recognize this file type.
Am i SOL on getting my audio books onto my iPod till the next libgpod comes out?

---

### Post by twright on 2008-03-28
i'm afraid you won't have much luck with .aa files because of the drm they include

you may be able to convert them to mp3 using this tutorial:
[http://www.chuckegg.com/how-can-i-convert-audiblecom-aa-files-to-mp3-audio-files/](http://www.chuckegg.com/how-can-i-convert-audiblecom-aa-files-to-mp3-audio-files/)

---

