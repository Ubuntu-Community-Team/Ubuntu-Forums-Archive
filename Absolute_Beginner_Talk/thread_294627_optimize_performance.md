---
title: "optimize performance"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by Fittersman on 2006-11-06
how can i optimize performance on ubuntu so it runs faster and make movies play better, the sound seems to outrun the video and the sound is getting increasingly farthur ahead of the video. How can i stop this from happeing?
and when i use vlc the sound and video is on the same part but the video is all choppy to keep up with the sound.

---

### Post by Mr. Matt on 2006-11-06
I find mplayer plays videos much smoother than Totem on my 700 Mhz Duron.  Perhaps try some different video players, it worked for me.

---

### Post by Imsati on 2006-11-06
As far as gneral performance, I've never really had a problem.

As far as the vidoe stuff, refer to the sticky at the top of this page concerning mp3, codecs, and the like. It'll link you to a very nice page where you can install all the proprietary formats to make things play smoother.

~Jay

---

### Post by Imsati on 2006-11-06
And for the record, I'm running KDE and prefer Kaffien for DVD/video playback and Juk for other music, if it helps any.

---

### Post by turbojugend_gr on 2006-11-06
You have a problem with your codecs, try installing the appropriate codecs for the format you are playing. Usually ffmpeg package (through synaptic) manages to paly most win32 codecs. What type of video are you trying to play, so I can help you further?

---

### Post by Imsati on 2006-11-06
And you probably already figured it out, but my in my last post when I said "refer to the sticky at the top of this page", I meant the top of the Absolute Beginner Forum page.

It'll tell you exactly what packages you need and how to install the w32codecs

---

### Post by jaytek13 on 2006-11-06
I'm not sure if this helps with video playback (I assume it does but I'm not sure), but if you have a Nvidia card you can make sure fast write and sba are enabled.

[http://doc.gwos.org/index.php/Nvidia_Driver_AGP_FastWrite_and_Side_Band_Addressing](http://doc.gwos.org/index.php/Nvidia_Driver_AGP_FastWrite_and_Side_Band_Addressing)

I'm not sure of the ATI counterpart, or if there is one.

---

### Post by adamkane on 2006-11-06
If you think it's a performance issue, and not a codec issue, make sure you have the optimized kernal files for your hardware. Ubuntu ships with an unoptimized 386 kernel. 

If you have an older system, this will give it a boost, and you will be able to run multimedia in the background.

Intel Pentium (Other than Pro or 486):

```

sudo apt-get install linux-686 linux-image-686 linux-headers-686 linux-restricted-modules-686

```

AMD K Series (Duron, Athlon, Sempron):
 
 ```

sudo apt-get install linux-k7 linux-image-k7 linux-headers-k7 linux-restricted-modules-k7

```

Reboot.

---

### Post by Fittersman on 2006-11-07
it is a performance issue, i have the codecs (as far as i know) and that last post, how do i tell what intel thing i have? (i have a sticker on the outside of the computer that says "intel inside" (with that little circle thing around it) "celron" i have a 2.6 GHz intel celron processor 512 ram

movies ran smooth on windows so i know i can run them at a good speed.

i dont know if 3D acceleration matters to videos but mine is not working and im trying to get it fixed on this forum page

[http://ubuntuforums.org/showthread.php?p=1729004#post1729004](http://ubuntuforums.org/showthread.php?p=1729004#post1729004)

---

### Post by adamkane on 2006-11-10
Use the Intel Pentium install.

For 3D to work, you need to install working ATI or nVidia drivers for your video card.

Automatix has a good nVidia installer. ATI is hairy to install on Ubuntu, but there are many howtos on the forums. Dapper detects my 3D cards well, so I am not up on the latest issues.

---

