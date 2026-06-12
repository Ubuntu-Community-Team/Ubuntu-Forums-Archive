---
title: "Having some...trouble with NVIDIA Legacy drivers and 3D support."
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by cubanresourceful on 2007-02-25
I just installed the legacy drivers, using the guide, but for some reason they do not work. How do I know? Because Chromium and Blob Wars: Command And Conquer do not even open. That is a sign of it not working, because when I did have 3D support (openSuSE), it would open.

Now, I was able to install and get them working correctly on openSuSE, but what is fustrating me is that its not working in Ubuntu Edgy Eft 6.10. Now, if anyone can help, feel free to. Here are some details on my system:

Toshiba Satellite 5205-S5151
Mobile Intel Pentium 4 Processor 2.20 GHz - M
1 GB DDR SRAM
32 MB DDR NVIDIA GeForce4 460 Go
15.0" SXGA+ diagonal TFT
Linux Ubuntu Edgy Eft 6.10 installed with GRUB

Is that enough information, or is more needed?

---

### Post by rusty4r on 2007-02-25
I used the envy script to get my old nvidia card to work.

Are you sure that the legacy driver is the one you need. I was thinking that a GeForce4 card would be on the 96xx driver which is the one I used on Dapper.

But, with Edgy I just used the Envy script, it chooses the right one for you.

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

Hope this helps

---

### Post by cubanresourceful on 2007-02-25
Thanks for the link. This "envy" can help when I screw up. But, I chose automatic, or option 1, and when it runs X Server, i see it white, then it starts to fade out into black. I can log in, and hear the log in sounds, but cannot see. Then I did Manual Install, tried the latest driver, same thing. Fade out effect. Tried the legacy driver, thats was the latest, like 96.xx, same thing, fade out effect. I then, installed the "old" legacy driver through manual, and guess what, no more fade effect thing, BUT no 3D support. Why does it not work, even though my GPU is supported?

---

### Post by rusty4r on 2007-02-25
I'm definitely no expert on this, but the first time I ran it I had no luck either but then I  chose the option for removing driver , option 2 I think, then chose option 1 and after restart I had 3d support.

---

### Post by cubanresourceful on 2007-02-25
Okay, I will do as you say. Heh, it worked on openSuSE, thats why I am puzzled. Because, as I see it, Ubuntu is superior to openSuSE in almost everyway. :D

---

### Post by cubanresourceful on 2007-02-25
Tried what you suggested, no go. Why is this happening? :(

---

### Post by cubanresourceful on 2007-02-25
Sorry for triple, but I just want to say, its now working perfectly. It seems that the "envy" installer would uninstall glx-legacy, and that there was my problem. By installing it, I now have 3D rendering support. :D Thanks for all the help!

---

