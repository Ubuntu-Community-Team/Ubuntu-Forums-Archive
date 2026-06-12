---
title: "png to avi?"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by muhkayoh on 2006-06-12
Hi,

I'm trying to use Stop Motion to convert a sequence of png images into an avi file, but so far I can't get the configuration bit worked out.  None of the presets work (and they all seem to reference jpgs, so maybe that isn't surprising), and I can't seem to figure out how to edit any of the presets to handle pngs.  Can anybody help me with that?  Or, maybe there's an easier way to convert pngs into avi?  I'm open to any and all possible solutions.

Thanks,

Matt Jordan

---

### Post by muhkayoh on 2006-06-13
Still wondering about this one, so bump...

---

### Post by uzi09 on 2006-06-13
i believe there are programs to do this for you.
a quick google search and i came across this:
> 
This Stop Motion capture program MotionMage was created by the BricksinMotion people. The freeware version includes ...full camera settings, auto-averaging, color MotionMageanalysis, frame delay, frame-order editing, onion skin display, audio playback, AVI-JPG-GIF, & PNG import, and AVI export. You can use MotionMage  with USB Webcam, DV Camcorders  or the ol' Analog Camcorders (if you have analog capture card). Again, this is the free version and so resolution choice will be limited but but seems like a good starter tool for learning Stop Motion. MotionMage is written in Java  and it uses the Java Media Framework for video functions. This means, it works with both PC-Windows and Unix/Linux  systems. (It has not been tested on Macs yet) According to software's author, this one may be a little more tricky to set-up. If you are somewhat computer literate, it may not hurt to at least try it as it does have good useful Stop Mo features. If you have any issues or questions, I do not know how responsive they are. Check it out MotionMage1.2

source: [http://www.stopmotionworks.com/stopmosoftwr.htm](http://www.stopmotionworks.com/stopmosoftwr.htm)

MotionMage website: [http://mywebpages.comcast.net/tomfoote3/BIM/id155.htm](http://mywebpages.comcast.net/tomfoote3/BIM/id155.htm)

let us know how well it works ;)

---

### Post by muhkayoh on 2006-06-13
Thanks, but the MotionMage free is limited to a tiny resolution that won't do.  I actually was aware of that option and I have been Googling for solutions.  It's how I found MonkeyJam, for instance, which works great on Windows, but so far is a no go for me on Ubuntu.  I've also tried something called ImageJ, which works but seems to have poor image quality on output, a problem I so far haven't been able to solve.

To be clear, when I said "Stop Motion" in the initial post, I was refering to the application by that name which I now have installed on my system.  And, for further clarity, here's the big picture of what I'm trying to do:

I'm making animated films using Inkscape and GIMP, outputting scenes as a series of png stills, converting each png batch into an avi scene (the step I'm having trouble with) and then hooking those scenes toegther and adding sound in an editor. 

I'm doing it this way because a) Inkscape is a really fantastic drawing program that allows me to get very natural looking results and, b) I'm really after a traditional cel animation look.

I'm aware of Synfig and have played with it a bit, but the vector approach it takes, while useful for cutting down work time, doesn't give the look I'm after.  I also see Ktoon is in development, but it seems too raw for my purposes (and in any event appears unable to equal Inkscape's drawing abilities).  I've also toyed with GIMP-GAP, but haven't been happy with the results there either.



Right now, I'm reading through the MEncoder documentation to see if I can get it to do what I need with respect to this png-avi thing.  MonkeyJam would be perfect, but, as I said, I can't get it to work for me using Wine.  (But I'm only two days into Ubuntu-land, so maybe that'll change.)

Anyway, thanks again for the response.

Matt Jordan

---

### Post by muhkayoh on 2006-06-13
A follow-up, fwiw.

I had also written one of the developers of Stopmotion and have now heard back from him.  It turns out that the settings I was using (slightly modified from the default settings) required MEncoder to be installed.  I had Mplayer and thus thought I had MEncoder, but apparently didn't.  I used Synaptic to install MEncoder and now I'm able to convert pngs to avi with Stopmotion.

Matt Jordan

---

### Post by bloodyserb on 2006-07-08
I can't find mencoder in synaptic, am I doing something wrong?

---

