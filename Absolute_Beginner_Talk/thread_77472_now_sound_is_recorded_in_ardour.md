---
title: "now sound is recorded in ardour"
date: 2005-10-16
forum: Absolute Beginner Talk
---

### Post by jasonpeinko on 2005-10-16
I have a cable running from my sound board to the the mic input on the comp.

i start jack and load ardour and when i try to record nothing happens. any ideas?

---

### Post by BoyOfDestiny on 2005-10-17
Yep. Try sudo killall esd. If this does the trick use the multimedia selector to change the input and output (alsa I'd guess). If you want to keep esd off, go to sound and uncheck start sound server...

Hope this works for you!

(disabling ESD has solved every sound problem on every machine I've put Ubuntu on... :) )

---

### Post by wishyjr on 2005-10-17
ok, is there a way of setting up the system to start Jack as the sound server or am i abit wrong there? im having a little trouble getting to grips with sound stuff. My Multimedia sound section shows that i have my Default sink output as ESD and my Default source input as OSS, can i ask is thsi desirable? it seems to work but lately ive been getting stuttery sound on video files.

I've got Ardour and jack installed. Ive managed to start it up but im just wondering if i need to sort out my sound settings properly before getting right into making music.


cheers

ps. sorry of the hijacking.

---

### Post by patrick295767 on 2005-10-17
i got helped to used : 

chmod 666 /dev/dsp
chmod 666 /dev/dsp1

to give permissions to my device for sound

also try : alsamixer 
use M key to un-/mute sound ...

I hope that will help you (maybe) !!

Courage !!

Pat'

---

### Post by jasonpeinko on 2005-10-17
ok still not working.
I have the following running:
qjackctl - with connection started
alsamixer
alsaplayer - does not open a window and does not take me back to command
ardour - with input set to alsa_pcm:capture_1

stilll nothing works.
When i have volume boosted it sound comes out my speekers from just talking to the mic when nothing is running.

could it be that i am using the sound bus off my motherboard? I have a turtle beach i could take off my other comp if that is the porblem

killall esd 

kills nothing and does nothing

---

### Post by jasonpeinko on 2005-10-17
[QUOTE=wishyjr]ok, is there a way of setting up the system to start Jack as the sound server or am i abit wrong there? im having a little trouble getting to grips with sound stuff. My Multimedia sound section shows that i have my Default sink output as ESD and my Default source input as OSS, can i ask is thsi desirable? it seems to work but lately ive been getting stuttery sound on video files.

I've got Ardour and jack installed. Ive managed to start it up but im just wondering if i need to sort out my sound settings properly before getting right into making music.


cheers

ps. sorry of the hijacking.[/QUOTE]

[ardour sound recording tutorial]("http://www.djcj.org/LAU/ardour/Basic_editing_howto.html")

---

### Post by jasonpeinko on 2005-10-17
plz help

---

### Post by BoyOfDestiny on 2005-10-17
[QUOTE=jasonpeinko]ok still not working.
I have the following running:
qjackctl - with connection started
alsamixer
alsaplayer - does not open a window and does not take me back to command
ardour - with input set to alsa_pcm:capture_1

stilll nothing works.
When i have volume boosted it sound comes out my speekers from just talking to the mic when nothing is running.

could it be that i am using the sound bus off my motherboard? I have a turtle beach i could take off my other comp if that is the porblem

killall esd 

kills nothing and does nothing[/QUOTE]

Well you would need to put sudo infront of it, and it would kill esd (which has a tendency to tie up stuff).

Did you try to look at the multimedia selector (it's in the menus). You can test the input/output of audio (and video)

---

### Post by jasonpeinko on 2005-10-17
[QUOTE=BoyOfDestiny]Well you would need to put sudo infront of it, and it would kill esd (which has a tendency to tie up stuff).

Did you try to look at the multimedia selector (it's in the menus). You can test the input/output of audio (and video)[/QUOTE]
i dont have a multimedia menu do you mean in ardour on ubuntu?

---

### Post by jasonpeinko on 2005-10-17
what i will do for now because i need recording by sunday is unless i get ardour or some other program to work i will just use windows to record and then i will edit with ardour

---

### Post by BoyOfDestiny on 2005-10-18
[QUOTE=jasonpeinko]i dont have a multimedia menu do you mean in ardour on ubuntu?[/QUOTE]

I mean in Ubuntu. I don't know if you are using the english language version but
System -> Preferences -> Multimedia selector. (going from memory). As I said about ESD, it still may muck things up even when not selcted... so try a sudo killall esd if you still have no luck after making changes in the multimedia selector...

Good luck!

P.S [http://www.dynebolic.org/](http://www.dynebolic.org/)
I haven't tried it, but it's a multimedia linux livecd.

---

### Post by jasonpeinko on 2005-10-18
ok found it but it gives me an error when i clcick test.

---

### Post by BoyOfDestiny on 2005-10-18
[QUOTE=jasonpeinko]ok found it but it gives me an error when i clcick test.[/QUOTE]

Try different settings and then click test? Keep the ones that work. If none work try sudo killallesd and try again.
If none of that works, give dynebolic a try.

[www.dynebolic.org/](www.dynebolic.org/)

Good luck.

P.S Sorry if I haven't been helpful. For sound I've only used Audacity. (and some fun players for sid, nsf, gbs, and like 150 amiga formats...)

---

### Post by joshpelkey on 2005-10-19
I use ALSA for both default sink and default source.  Before you run ardour, open up the terminal and type "killall esd."  Also, make sure that your microphone is set for audio capture.  I forgot to do this once and it's frustrating knowing the solution is so simple.  Do this through the alsa mixer under the "capture" tab.  Once you've done that, open up ardour and test it out.

---

### Post by jasonpeinko on 2005-10-19
there is no captrue tab

---

### Post by jasonpeinko on 2005-10-19
is audacity easy to use and set up?

---

### Post by joshpelkey on 2005-10-19
Yes, audacity is easy to use and set up.  Try going to the menu applications --> Sound & Video --> Volume Control.  In volume control select file --> change device --> the one with (alsa mixer).  Now check for a capture tab.

---

### Post by jasonpeinko on 2005-10-19
no there is not one. When i have my speacers hooked up sound does travel through the computer and out the speakers

---

### Post by joshpelkey on 2005-10-19
There isn't an (alsa mixer) selection, or there isn't a capture tab?  What are you running this on?  Laptop?  PC?  What are you using for sound?

If you are in the alsa mixer make sure under Edit --> preferences you have the microphone box checked.

---

### Post by jasonpeinko on 2005-10-19
there is no edit or anything in alsamixer it is just a bunch of things that u use the arrow keys to navigate.

---

### Post by joshpelkey on 2005-10-19
Ok, you've typed "alsamixer" in the console I think (rather than going to applications --> sound & video --> volume control.  Anyhow, if you've used "alsamixer" command, just scroll over to the option for "Mic"  and make sure it isn't muted.  If it's muted you will see "MM" in the lower box.  To unmute press the 'm'  key.

---

### Post by jasonpeinko on 2005-10-19
ok

[http://www.djcj.org/LAU/quicktoots/toots/Jack_Ardour/](http://www.djcj.org/LAU/quicktoots/toots/Jack_Ardour/) 
im using that tutorial 
and when i have jack running and i try and open alsaplayer nothin will show up

---

