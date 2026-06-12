---
title: "[SOLVED] Sound"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Camrygrl on 2008-01-21
Is there a way to hear the sound from a website and from music in the computer at the same time?  For instance, I am playing games and want to hear music at the same time 
  ](*,)   I have tried different variations in the sound menu, but no joy.

          
Thanks!

---

### Post by tophcito on 2008-01-21
Hello!

You would be in need of a sound daemon for that task. (For background info on sound daemons check out: [http://en.wikipedia.org/wiki/Sound_server]("http://en.wikipedia.org/wiki/Sound_server"))

In theory, the sound daemon creates something like an artificial sound card, all programs put their output to. It then mixes these different sounds together, and forwards them to your real soundcard.
Gnome, and thus Ubuntu should allready come with ESD preinstalled.

Strangely enough, a quick forums  search only provided a HOWTO on PulseAudio, which can do the same. You can find that HOWTO here [http://ubuntuforums.org/showthread.php?t=548178]("http://ubuntuforums.org/showthread.php?t=548178")

I think ESD should be easier to set up, so I would advise you to rather stick with it. Sorry I could not find more right now, its 3:30 am at my place. If I find more on that, I'll post it here. In the meantime, googling for ESD should provide you some insight too.

---

### Post by Camrygrl on 2008-01-21
Thank you for your help at 3am!  
I have sound events and movies and movies set to ESD.  Should it be playing both?

Thanks!

---

### Post by tophcito on 2008-01-21
glad to be helping. ;-)

I'm myself rather new to Ubuntu, so I can only tell u this:
In my setup, where I did not change anything in particular from the original install, sound notification of events works even when watching a movie (which can be really annoying, if my computer starts beeping for new mail, just before the killer reaches the victim). So I think in your case, it should work similarily.

But perhaps there somebody more competent on these forums than me?

---

### Post by Camrygrl on 2008-01-22
In trying to remedy this problem I have found that I cannot play music thru Rythm Box.  I get an error that says "cannot connect to server."  I was playing the music before in Totem.

---

### Post by tophcito on 2008-01-22
Hey,

sorry for the late answer, i had to get some sleep eventually.

I was looking some more and found two forum posts that deal with similar problems:

[http://ubuntuforums.org/showthread.php?t=75237]("http://ubuntuforums.org/showthread.php?t=75237")
[http://ubuntuforums.org/showthread.php?t=84371]("http://ubuntuforums.org/showthread.php?t=84371")

So, I think you should check, that ESD is your default Multi Media System. To do that, go to System -> Preferences -> Multimedia System Selector. There, set your audio's default output plugin to ESD. In a next step, try to set everything where there is such an option in System -> Preferences -> Sound to using ESD.

Then to be on the safe side, log out, and log in again, or reboot. Just to make sure that everything really gets loaded the way it is supposed to.

Then all the application where you cannot configure it seperately, should play their sound via ESD, thous be automatically mixed. Application where you can change the output settings, would have to be directed to use the esd output. 

I will try to set my system to ESD now, and come back with the experience i make.

cheers.

---

### Post by tophcito on 2008-01-22
Okay, I just got back from trying to that to my system too.

Here is what I did:

1. Change Multimedia System to ESD (System -> Preferences -> Multimedia System Selector)

2. Go to a Terminal (Applications -> Accessories -> Terminal) and type into that window 
```
sudo apt-get install esound 
``` (that actually installs the sound server, the programs earlier where reporting they could not connect to)

3. Change Gnome Sound Output to ESD (System -> Preferences -> Sound; there change everything that has this option to ESD)

4. Reboot (so that the soundserver got started automatically, as it will be from now on)

5. Test: Started Totem movie player and Rythmbox, both played sound simultaneously.

I hope that helps you.

---

### Post by Camrygrl on 2008-01-22
Did that, didn't work.  In fact..when I rebooted my screen is set at 680x480 now with no other options to change it.  Which doesn't make sense because I didn't mess with any of the visual stuff.  I don't have a multimedia option.  I went to preferred applications and the only options are Internet and system.  I am running Feisty if that has anything to do with the sound options.

---

### Post by Camrygrl on 2008-01-22
ok, my bad.  I have sound for rythmbox now but it doesn't mix pogo sounds and player sounds.  It's one or the other.  

Thanks for your help

---

### Post by tophcito on 2008-01-22
okay, feisty it is.

I am using the gutsy, gitsy whatever g animal that was. So my advice was speaking for the g version (7.10) I cannot really talk about feisty. sorry. 

But there is the Beginner Team, that is certainly able to tend to your problems, they have more experience, also with the different versions of ubuntu.

You can find them here:
[http://ubuntuforums.org/showthread.php?t=378426]("http://ubuntuforums.org/showthread.php?t=378426")

Perhaps its wisest to send a private message to one of the team members. I am sure they can help you.

Sorry that I couldn't. Good luck.

---

### Post by Camrygrl on 2008-01-22
I rebooted and screen res went back to normal.  Thanks for your help.  I really appreciate it!  Under Applications>Sound and Video I have an Gnome Alsa Mixer that I don't remember having before.  I am trying different options with that.

---

### Post by Camrygrl on 2008-01-22
Ok.  That's not working.  Anybody else have any clues?

---

### Post by Camrygrl on 2008-01-22
I ended up with no sound again so I just reinstalled Feisty.

---

