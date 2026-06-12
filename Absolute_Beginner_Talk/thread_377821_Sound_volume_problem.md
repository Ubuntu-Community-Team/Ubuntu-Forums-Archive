---
title: "Sound volume problem"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by goodbyewindows on 2007-03-06
Im running Edgy on a laptop and I have an annoying bug: when I turn the volume all the way down the volume thing tells me that it's muted but I can still hear music etc...

---

### Post by old_geekster on 2007-03-06
I have the same problem.  It doesn't hinder my use of my players, so I simply have ignored it.

The thing that I don't like, however, is not being able to control the volume from one source.  I have to adjust three separate controls.  I set Master and Surround to full volume and adjust both with PCM.  This is extremely inconvenient, because I must access Alsa Mixer to make the adjustment.

Hopefully, we will both get an answer to your problem.  I replied because I know that misery likes company.:lolflag:

---

### Post by hppyfngy on 2007-03-09
Well, I'll join the crowd.  My master volume control doesn't effect the volume output, even though it shows the controller on the screen when I adjust it.  

I can control volume within apps, like Amarok, via the roller on the mouse, but there is a controller on my Plantronics headset, and it "looks" like it's working, i.e. the volume icon appears and moves up and down, but it doesn't change the volume.  There must be a master volume somewhere or a way to set alsa to the master, but I don't know what it is.

So, bump...:popcorn:

---

### Post by HeelsFan on 2007-04-20
I'm in the same boat.  I now can't control the main system volume using the volume control in the systray or the volume keys on my keyboard.

Both worked in Edgy and I upgraded to Feisty today.  I did go into alsamixer and adjust the levels of my surround sound speakers, but that was all I did.

If I double click the volume control icon in the systray I can adjust the PCM volume and it works properly, but I can't associate the volume control with the PCM for some reason.  I have right clicked the icon and had selected preferences and told it that I wanted it to control PCM, but have not had any success here.

Anyone with a command line fix to associate volume control with PCM?

---

### Post by HeelsFan on 2007-04-20
I think I resolved my issue.  I had to go to System > Preferences > Sound and select PCM there.  Not sure why it wouldn't work from the volume control preferences in the systray, but hey now it works so can't complain too much.

---

### Post by hencke on 2007-04-21
If you have the same problem in KDE:

Open kmix, right click on the systray icon and choose the right option from "Select Master Channel..."

Source:
[http://ubuntuforums.org/showthread.php?t=413318&highlight=keyboard+volume+control](http://ubuntuforums.org/showthread.php?t=413318&highlight=keyboard+volume+control)

---

### Post by canalegrande on 2007-10-13
> **HeelsFan said:**
> I think I resolved my issue.  I had to go to System > Preferences > Sound and select PCM there.  Not sure why it wouldn't work from the volume control preferences in the systray, but hey now it works so can't complain too much.

Similar here, but I had to select "surround" on my Acer 5920 Laptop

---

### Post by errenay on 2007-10-31
@hencke - Thank you for the idea. It works for me, but only "in half". I could control volume via the Kmix applet (systray icon) but the wheel in my laptop doesn't do anything. When I touch the volume wheel there is special window with "volume" but it doesn't change the volume.
@canalegrande - I have the same laptop as you. Did you experience problems with the wheel?
Now I have Kubuntu 7.10. Everything worked fine in Kubuntu 7.04.

---

### Post by Hailthorn on 2008-04-08
> **HeelsFan said:**
> I think I resolved my issue.  I had to go to System > Preferences > Sound and select PCM there.  Not sure why it wouldn't work from the volume control preferences in the systray, but hey now it works so can't complain too much.
Thanks! You fixed my problem. :D

---

