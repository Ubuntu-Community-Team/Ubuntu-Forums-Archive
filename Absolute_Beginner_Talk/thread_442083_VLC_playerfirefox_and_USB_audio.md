---
title: "VLC player/firefox and USB audio?"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by tabithaboof on 2007-05-13
I have a USB audio device which I use because the headpphone jack on my Laptop doesnt work very well. I have changed Xmms and Movie player to output through the USB audio adaptor. I have also altered the default sound device under system, preferences, sound to output everything through USB but Firefox and VLC insist on playing through the Laptops little internal speaker.

I have looked under output modules advanced options for VLC player and it doesnt have any option for USB device output and I cant find anything about firefox's sound devices at all. Anyone able to help?

---

### Post by chaag on 2007-05-17
I have the same problem. Though my concern is only Firefox. I have tried playing with
/etc/firefox/firefoxrc

to no avail.

Other media players use my Perferences > Sound > USB Audio settings fine. Why not firefox?

thanks

---

### Post by elektronaut on 2007-06-02
I was so annoyed by the fact that I couldn't hear audio through the usb sound device when using firefox, that I finally switched to Epiphany. I can highly recommend it. You get the same browsing experience, plus an interface that integrates with GNOME and working audio.

---

### Post by brammers456 on 2007-12-25
Hello

I have had the same issue with VLC, in that it doesn't seem to recognise my USB audio device.  I tried going into the settings to adjust the audio output settings to recognise my device as an ALSA device, to no avail.  However upon looking through the responses 'Google' found, I worked out the answer (I would like to stress though it was thanks to the "USB Audio / Speakers with Ubuntu Linux" article on the "http://www.michaeldolan.com" that helped me work out the solution to this problem)


To adjust which audio output VLC uses, just follow these steps:

1) Select "Settings" in the toolbar at the top of the VLC window, follow that by selecting "Settings" 

2) You will now be presented with the Preferences window, with a list of choices in the immediate left "Audio, Video, Input / Codecs" .. etc.  Select the arrow pointing to the "Audio" option.

3) Several more options will now appear "Filters, Output Modules, Visualisations".  Select the arrow pointing to the "Output Modules" option

4) Three more options will appear "File, ALSA, OSS" Note. There are no arrows next to these.  Select the "OSS" option

5) You will now be presented with a window titled "Linux OSS audio output" with the current OSS device being used for the sound.  It should look something like this "OSS DSP Device"  with  "/dev/dsp" in a white box next to it (This is the current OSS device being used).  Put the following in the white box "/dev/dsp1", and select the "Save" button at the bottom of the window.

6) Close VLC and try playing an audio or video file

If you have any problems just go to the website shown in the top paragraph and have a look at the article "USB Audio / Speakers with Ubuntu Linux"

Apologies to those who already know many of these steps, these are just to aid the less experienced users out there.

I hope this helps and thanks to "Michael Dolan" for helping me solve this problem.

Brammers456

---

### Post by Thierrylafronde on 2008-01-05
Thank you enormously, I had struggled for a week with this one and now it works like a charm.
Thank you again to both of you. (you and MD that is).
:smile::smile:

---

### Post by Valir on 2008-06-08
Hi, 

Is there a solution for firefox (3) yet, usb headphones works well for everything except firefox,


best

---

