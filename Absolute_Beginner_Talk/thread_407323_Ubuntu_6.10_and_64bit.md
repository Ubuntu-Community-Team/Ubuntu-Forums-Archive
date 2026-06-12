---
title: "Ubuntu 6.10 and 64bit"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by makinasvp on 2007-04-12
Hello everybody.
I have uninstalled Windows for life today. Good bye Bill Gates. Will miss you...not.
I installed Ubuntu 6.10 and truthfully I couldn't be any happier. The interface is just amazing.
System specs:

-AMD FX-60 Dual-Core processor
-1 500GB Maxtor HD (@72,00rpm)
-2x7800GTX GeForce Graphic cards
-Asus Deluxe Sli Ready mobo
-4GB of RAM (CorsAir)

Now, today I have successfully installed nvidia drivers and Beryl. And WOW Beryl is just amazing. I got to play with it a little bit and understand how it works. 
Ubuntu + Beryl > OSX, Windows XP, Windows Vista by far!!!!!

Here are my questions. Since my Ubuntu is the 64bit version. I am a little sad because I havent figured out how to play mp3 music files into my computer, nor can I watch any youtube videos... :(
I successfully installed Wine HQ and now I am in the process of installing Steam and CounterStrike Source. So far so good.
But as far as for playing mp3s or youtube videos. Can someone please help me? I am so new to this and have absolutely no clue what I am doing... lol

Help!!!

---

### Post by jem7v on 2007-04-12
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) should help you for most media codecs.  You'll probably have trouble installing Flash, though, because you're running the 64-bit version and, well, that makes it much more complicated.  (Search the forums or Google for help with that.)

---

### Post by makinasvp on 2007-04-12
> **jem7v said:**
> [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) should help you for most media codecs.  You'll probably have trouble installing Flash, though, because you're running the 64-bit version and, well, that makes it much more complicated.  (Search the forums or Google for help with that.)

I have tried and did research for installing Flash, and made probably 3 different attempts on installing it. No luck so far... Unsuccessful.
I am going to check out the url you gave me for media codecs right now. 
Hope to hear some more from you guys. :)

---

### Post by deadgobby on 2007-04-12
If I was you. I would install 32 bit Ubie instead of 64. There is still much needed work to be done on the 64 bit kernal. Most people install Automatix or Easy Ubuntu for all the codecs at once.
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)
 It seems Automatix is down for now and just google it.

Gobby

---

### Post by makinasvp on 2007-04-12
> **deadgobby said:**
> If I was you. I would install 32 bit Ubie instead of 64. There is still much needed work to be done on the 64 bit kernal. Most people install Automatix or Easy Ubuntu for all the codecs at once.
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)
 It seems Automatix is down for now and just google it.

Gobby

Ok, and would my system be compatible with the 32 bit Ubie?
Oh and is easyubuntu compatible only for 32 bit or for 64 bit as well?

---

### Post by RomeReactor on 2007-04-12
Hi. To play mp3's in Rhythmbox, you need to install **gstreamer0.10-plugins-ugly**. To get flash going, i agree that using Ubuntu 32-bit is the easiset way; most likely you won't notice a difference in performance. And it looks like your AMD FX-60 Dual-Core [does support 32-bit]("http://www.neoseeker.com/Articles/Hardware/Reviews/amdfx60/").

---

### Post by makinasvp on 2007-04-12
> **RomeReactor said:**
> Hi. To play mp3's in Rhythmbox, you need to install **gstreamer0.10-plugins-ugly**. To get flash going, i agree that using Ubuntu 32-bit is the easiset way; most likely you won't notice a difference in performance. And it looks like your AMD FX-60 Dual-Core [does support 32-bit]("http://www.neoseeker.com/Articles/Hardware/Reviews/amdfx60/").

WOOHOO!!! I cannot wait to go home from work (I work the nightshift at godaddy.com).
The thing is, I hope I will be able to install Beryl and Steam (CounterStrike Source) again, because when I need, I think it was pure luck... lol
But since I'm going to switch to the 32bit version, wouldn't it be easier anyways? Maybe? ;)

---

### Post by deadgobby on 2007-04-12
> **makinasvp said:**
> Ok, and would my system be compatible with the 32 bit Ubie?
Oh and is easyubuntu compatible only for 32 bit or for 64 bit as well?

Yes, your system would be fine with installing 32 bit for AMD. Here is a link 
[https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=amd&titlesearch=Titles](https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=amd&titlesearch=Titles)
 I would install 32 bit and then install Easy Ubuntu. As I said before. Most programs in Linux is 32bit. When the software world has better support for 64 bit. I would run with it.

---

### Post by makinasvp on 2007-04-12
> **deadgobby said:**
> Yes, your system would be fine with installing 32 bit for AMD. Here is a link 
[https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=amd&titlesearch=Titles](https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=amd&titlesearch=Titles)
 I would install 32 bit and then install Easy Ubuntu. As I said before. Most programs in Linux is 32bit. When the software world has better support for 64 bit. I would run with it.

Well thank you so much for your help. I really appreciate it. I did have a hard time installing my nvidia drivers on the 64bit version. I just hope it wont be as painful with the 32bit edition lol. Thanks again!!!

---

### Post by RomeReactor on 2007-04-12
To install drivers for your Nvidia card, you can just use the ones in the repositories through Synaptic (**nvidia-glx**), or use [tseliot's Envy]("http://albertomilone.com/nvidia_scripts1.html"). Then there's also [this thread]("http://ubuntuforums.org/showthread.php?t=301499").

---

### Post by makinasvp on 2007-04-12
> **RomeReactor said:**
> To install drivers for your Nvidia card, you can just use the ones in the repositories through Synaptic (**nvidia-glx**), or use [tseliot's Envy]("http://albertomilone.com/nvidia_scripts1.html"). Then there's also [this thread]("http://ubuntuforums.org/showthread.php?t=301499").

oh ok, and it should be a lot easier than the 64bit version right? Because on the 64bit I had to do CTRL+ALT+F1 and do all kinds of stuff there...

---

### Post by RomeReactor on 2007-04-12
The times I've encountered problems installing the nvidia drivers are when trying the ones I downloaded from the nvidia page. Other than that, it's just been a matter of running **sudo nvidia-glx-config enable** in the terminal after installation to get the drivers working. I also tried Ubuntu 64 bit once and didn't have a problem installing the nvidia driver with Synaptic; however, my card is just a 6200. Seeing as you also want flash working, though, i do suggest Ubuntu 32-bit; it'll be easier for you on all fronts.

---

### Post by makinasvp on 2007-04-12
> **RomeReactor said:**
> The times I've encountered problems installing the nvidia drivers are when trying the ones I downloaded from the nvidia page. Other than that, it's just been a matter of running **sudo nvidia-glx-config enable** in the terminal after installation to get the drivers working. I also tried Ubuntu 64 bit once and didn't have a problem installing the nvidia driver with Synaptic; however, my card is just a 6200. Seeing as you also want flash working, though, i do suggest Ubuntu 32-bit; it'll be easier for you on all fronts.

Thank you so much, and thank you very much for the quick responses. I love this forum!!

---

