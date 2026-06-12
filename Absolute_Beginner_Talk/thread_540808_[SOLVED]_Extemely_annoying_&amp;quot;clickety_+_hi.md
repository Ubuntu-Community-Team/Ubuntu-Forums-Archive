---
title: "[SOLVED] Extemely annoying &amp;quot;clickety + hissing&amp;quot; sound from inbuilt speakers!!!"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-09-02
HI there all
I don't have Ubuntu on other machines so I can't compare right now.
Using my Dell laptop (see specs below for details) and there's this most horribly annoying clickety / hissing sound coming from the speakers, I'm 100% sure the inbuilt speakers are not broken as I was using it with XP & Vista just a week ago before my transition to Feisty.

Details:
Hissing (slight brumming, like bad interference) sound are constant and always there.

Clickty sound always when scrolling, going back / forward in browser or CPU under work load.

===================================================

Please note: These sounds are restricted to the inbuilt speakers only and are there even when the headphones are plugged into the jack!!! (normally headphone usage should cut off all sounds from inbuilt speakers)

This just seems to me like as if the sound driver is the culprit here!

Any suggestions?

Thanks

(note: these sounds are fairly low, but extremely annoying to me as my hearing is still pretty good) :roll:

---

### Post by SOULRiDER on 2007-09-02
I used to have that problem in windows, i never knew how to fix it or what it was causing it. In ubuntu i used to have some noise but muring the microphone did it for me.

---

### Post by Richardky on 2007-09-02
open your volume control panel - and uncheck analog/Digital Output Jack
and your sound problem should go away :)

if you cant find the output jack option listed -  in your sound control panel click on edit tab then preference check mark (tone) 

you now will have a extra panel viewable in your sound control panel that says switches -  uncheck analog/Digital Output Jack option.

---

### Post by MozartlovesUbun2 on 2007-09-02
> **Richardky said:**
> open your volume control panel - and uncheck analog/Digital Output Jack
and your sound problem should go away :)

if you cant find the output jack option listed -  in your sound control panel click on edit tab then preference check mark (tone) 

you now will have a extra panel viewable in your sound control panel that says switches -  uncheck analog/Digital Output Jack option.

In the place where you tell me to go I have the following options in which 2 are checked:

desktop>right click volume>open volume control>edit>prefernces

1 Master (checked)
2 PCM     (checked)
3 Capture
4 Capture Mux
5 Input Source

================

if I go

System>Preferences>Sound

it opens a different window called "sound preferences" with 3 tabs
Devices / Sounds / System Beep

================

so please what should I do?

---

### Post by Zootropo on 2007-09-02
It may be because of the microphone but a lot of 6400s and 9400s are well known for having this issue.

---

### Post by MozartlovesUbun2 on 2007-09-02
> **Zootropo said:**
> It may be because of the microphone but a lot of 6400s and 9400s are well known for having this issue.

Hmmm... I see, well I hope there's some way around it, by the way I don't have any mic attached, does that make any difference?

I'ld like to read up a bit on this issue, would you still have any links to where you've heard of it before as you mentioned it's a known issue.

thx

---

### Post by Duck2006 on 2007-09-02
> Hmmm... I see, well I hope there's some way around it, by the way I don't have any mic attached, does that make any difference?

Is the mic inbuild on your laptop?

---

### Post by alienexplorers on 2007-09-02
I have external speakers on my desktop and I have the same sound problem.  When I scroll the screen or during disk access I get a humming and cracking sound from the spaekers.  When I disconnect them and hook up headphones I have the same sounds there too.

I also do not have a microphone hooked up and I have it muted in preferences anyway.

---

### Post by MozartlovesUbun2 on 2007-09-02
> **Duck2006 said:**
> Is the mic inbuilt on your laptop?

hehe, no that would be cool from Dell to include a built in mic.

nope, sorry no built in mic that i know of, it has a jack input thingy to attach one if needed.

=======

as mentioned above I get these annoying sounds only from the built in speakers, not the headphones. But funnily even when the headphones are plugged in the inbuilt speakers still keep making those noises.

---

### Post by JayBachatero on 2007-10-16
I have a Dell Inspiron 1501 laptop and after upgrading last night to Gutsy I get this annoying sound.  I was using 7.04 for a while and never had this problem.  It's starting to piss me off. When ever i hover over a link or scroll I get system sound.  Hopefully someone can find a fix for this.

---

### Post by Wiebelhaus on 2007-10-17
Same here , it's driving me crazy.

---

### Post by Wiebelhaus on 2007-10-17
Well ,  hope the 7.10 reinstall will fix it , this is a retarded bug.

---

### Post by Belyel on 2007-10-17
The problem isn't limited to Dell machines.  I have the same problem on my Acer TM8200.  I think the problem is related to the video pipeline, not the speakers.  Ubuntu uses a lot of OpenGL (or similar) for the 3D effects and drawing windows on the screen.  When you are scrolling, you are basically getting X to redraw the window a whole bunch of times, and each of those redraws causes some sound.

If you have windows, you can test this out by using one of the screensavers that uses openGL (I think 3d pipes, flower box, etc) and see if you get the noise.  I noticed it most prominently when I started programming openGL in visual studio; when I run my programs, my compuer screams.  I don't think it is damaging, but it is very obnoxios.

---

### Post by Wiebelhaus on 2007-10-19
> **Belyel said:**
> The problem isn't limited to Dell machines.  I have the same problem on my Acer TM8200.  I think the problem is related to the video pipeline, not the speakers.  Ubuntu uses a lot of OpenGL (or similar) for the 3D effects and drawing windows on the screen.  When you are scrolling, you are basically getting X to redraw the window a whole bunch of times, and each of those redraws causes some sound.

If you have windows, you can test this out by using one of the screensavers that uses openGL (I think 3d pipes, flower box, etc) and see if you get the noise.  I noticed it most prominently when I started programming openGL in visual studio; when I run my programs, my compuer screams.  I don't think it is damaging, but it is very obnoxios.

Thanks for the explanation man , any idea how to silence it?

---

### Post by pacsum on 2007-10-20
> sudo gedit /etc/modprobe.d/blacklist

Then paste this command **blacklist pcspkr** at the end of the file and save it.

If not try this one > sudo modprobe -r pcspkr
That should do it.

---

