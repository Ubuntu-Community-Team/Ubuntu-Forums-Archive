---
title: "[SOLVED] would like to display laptop image on television monitor"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Amander on 2008-01-01
I have an Acer Aspire 3680 with an S-cable outlet. Is there a way to display what is on my laptop on the tv monitor, which also has an S-cable outlet? Is there a specific application, or is it purely information in-out via cables?

Since I made the switch to Ubuntu in August, this forum has been helpful countless times. For this, I thank you.

---

### Post by JoshuaRL on 2008-01-01
What type of graphics card do you have?  If you have the right driver installed and that is one of the options that it supports, then it should work.

---

### Post by bazzawill on 2008-01-01
This is handled by the graphics card driver so you will need to install the restricted drivers for either nvidia or ati. Which if you are using gutsy should be pretty easy with the restricted drivers manager in system -> administration -> restricted drivers manager. Then so long as you have done that nvidia has an application that helps although for some reason it's not in the menu. So you need to open a run dialogue alt+f2 or a terminal and type:
```
gksudo nvidia-settings
```
in xserver display configuration you can setup how you'd like to configure your tv as a display.

---

### Post by JoshuaRL on 2008-01-01
Well, I don't think that will work bazzawill.  From what I've found, I think the Acer Aspire 3680 has an Intel GMA 950 video card.  However, since it's pretty new and seems to be well supported, I think it may work with Svideo.  Honestly, you should probably just try it Amander.  There's a Function button on mine and a hotkey on the keyboard that switches on the CRT/LCD/Svideo.  You might see if you have something like that, and if not go into Settings>Administration>Screens and Graphics.  (Sorry if the directions aren't exactly correct, I run Xubuntu and the menus are a little different.)  If you're connected to a TV through Svideo, see if there's any options in there.

---

### Post by twin_57103 on 2008-01-01
I have often done this on my Windows laptop, although I have not tried it with Ubuntu.  On my laptop, it is a simple matter of plugging in the S-video cables, then rebooting (I actually use an adapter to RCA to run on older TVs).  I'd suggest you simply plug it in, reboot, and see what happens.

I've also seen several gadgets recently that, while considerably more expensive, are intended to adapt a computer output (probably VGA) to any TV - they might be Windows-only; I'm not sure.  They've been displayed near the TV tuner cards in the store.

---

### Post by Amander on 2008-01-06
Original poster here:

:**JoshuaRL**
*What type of graphics card do you have?*
- the sticker on the exterior of the laptop indicates that I have an Intel GMA 950 graphics card, but the system-->admin-->screen window indicates that it is an Intel 945 graphics card. (screen shot following)

*here's a Function button on mine and a hotkey on the keyboard that switches on the CRT/LCD/Svideo.*
 I do have a Function button and hotkeys on my laptop but I am unsure as to what each one does.  The F5 button has two screens sitting side-by-side: the left screen is an outline with a "blank" interior; the right screen is an outline with a "full" interior. That seems like the best option for the option switcher.

*if not go into Settings>Administration>Screens and Graphics.*
These are the screenshots from that procedure:

[IMG]http://img.photobucket.com/albums/v324/Manderpants/screen-graphics1.png[/IMG]

[IMG]http://img.photobucket.com/albums/v324/Manderpants/screen-graphics2.png[/IMG]

**Bazzawill**
[I]So you need to open a run dialogue alt+f2 or a terminal and type:
Code: 
gksudo nvidia-settings[/I]

And a screen shot when I ran that code:
[IMG]http://img.photobucket.com/albums/v324/Manderpants/terminal.png[/IMG]

From the Ubuntu Help Center included with my 7.10 :
[SIZE="1"]The nv driver supports PCI, PCI-Express and AGP video cards based on the following NVIDIA chips: [/SIZE]  (nvidia seems to have nothing to do with my laptop is the assumption I am making here)

**Twin-57301-**
*On my laptop, it is a simple matter of plugging in the S-video cables, then rebooting*

I will try that directly and report back with the result.

-----Thanks, everyone, for chiming in with your suggestions and experiences.

---

### Post by JoshuaRL on 2008-01-06
I have a laptop that I've configured with an Intel card, although not nearly that new.  From what I remember there are two Intel drivers.  One that is stable, and one in development.  You might try going into Screens and Graphics and click the Graphics tab.  Then choose on that menu the other driver and Test it.  The older HP laptop I tried that on worked better on the stable then the development and it might be the same for you.  Or maybe not.

---

### Post by Amander on 2008-03-13
I'd like to report success (and now I'll have to figure out how to mark this one as solved).

As previous posters mentioned "just try it".  I'll state exactly what I did and what happened.

Laptop: off
TV: off

Plugged s-video cable into both laptop and  tv

Turned on laptop, turned on tv.

Chose tv function to switch from satellite/dish option to "s-vid" option

Voila, there, I had a screen. My laptop screen had an odd anomaly where  the  toolbar (upper and lower) did not extend all the way to the right. The icons were all shoved over to the left and much more crowded than usual.

The only sad part is that only the video carried from the laptop to the tv; the sound did not.  I'll have to invest in a set of plug-in speakers. 

By the way, what *does* s-video cable mean? *Sound+*-video cable?

THANKS AGAIN FOR ALL YOUR HELP!!!

---

### Post by remu on 2008-03-13
It stands for Super-Video if I'm not mistaken.
To get sound working, you can get this cable that has a stereo (headphone) cable on one side, that splits into rca ends on the other (the red and white ones). If you plug the headphone end into your laptop, and the red and white ones into the proper input on the tv along with the s-video, that ought to work for you.
Good luck.

---

### Post by arekkusu on 2008-03-13
Separate video, abbreviated S-Video and also known as Y/C (or erroneously, S-VHS and "super video") ....

Just check the wikiepdia page: [http://en.wikipedia.org/wiki/S-Video](http://en.wikipedia.org/wiki/S-Video)
:)

While it wasn't the case here I always found funny how many ppl mistake S-VHS and S-Video. S-VHS being a type of video tape !

And yes, a Minijack to RCA connector will do fine for the audio

---

### Post by Amander on 2008-03-15
[SIZE="4"]Thank you both to remu and arekkusu for the follow-up sound/cbale questions![/SIZE]

I appreciate it, and all the help *everyone* gives in this place. My next task is to get my husband to make the full switch from Windows to Ubuntu.

---

