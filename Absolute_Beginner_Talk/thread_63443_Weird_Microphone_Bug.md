---
title: "Weird Microphone Bug"
date: 2005-09-07
forum: Absolute Beginner Talk
---

### Post by aysiu on 2005-09-07
I knew I was going to jinx myself by saying everything on my eMachines computer worked with Ubuntu straight away. The sound worked. The video card worked. Even the 8-in-one media card reader worked. CD-writer worked. DVD-writer worked. USB worked.

So I'm playing around with Skype now, which installed flawlessly as a .deb, and I can't get the microphone to work. I've tried using just about every configuration I can think of in Volume Control--even changing from [NVidea nForce2 (Alsa Mixer)](http://i22.photobucket.com/albums/b337/psychocats/5ae8e86b.png) to [Realtek ALC650F (OSS Mixer).](http://i22.photobucket.com/albums/b337/psychocats/c9a993aa.png) 

I did a few searches, but I didn't find anything helpful:

[http://66.102.7.104/search?q=cache:uxL_tRnkhaIJ:ubuntuforums.org/showthread.php%3Ft%3D13603+site:ubuntuforums.org+skype+microphone&hl=en&lr=lang_en](http://66.102.7.104/search?q=cache:uxL_tRnkhaIJ:ubuntuforums.org/showthread.php%3Ft%3D13603+site:ubuntuforums.org+skype+microphone&hl=en&lr=lang_en)
[http://66.102.7.104/search?q=cache:_cS0EWN_9nAJ:ubuntuforums.org/archive/index.php/t-21186.html+site:ubuntuforums.org+skype+microphone&hl=en&lr=lang_en](http://66.102.7.104/search?q=cache:_cS0EWN_9nAJ:ubuntuforums.org/archive/index.php/t-21186.html+site:ubuntuforums.org+skype+microphone&hl=en&lr=lang_en)
[http://66.102.7.104/search?q=cache:WmXG6g4GFLAJ:ubuntuforums.org/showthread.php%3Ft%3D13709+site:ubuntuforums.org+skype+microphone&hl=en&lr=lang_en](http://66.102.7.104/search?q=cache:WmXG6g4GFLAJ:ubuntuforums.org/showthread.php%3Ft%3D13709+site:ubuntuforums.org+skype+microphone&hl=en&lr=lang_en)

Here's the rub: it works perfectly fine in Mepis, so it's not a Windows/Linux thing. I'm wondering whether it's a Gnome/KDE thing or a Ubuntu/Mepis thing or even a Hoary/Breezy thing (I'm using Breezy now).

Any ideas of what I should try or any more details I should give that will help people help me? I'd really like to try out this Skype thing, and I'd hate to have to go back to Mepis (even though it is a great distro).

Thanks in advance...

---

### Post by poofyhairguy on 2005-09-08
[QUOTE=aysiu]I knew I was going to jinx myself by saying everything on my eMachines computer worked with Ubuntu straight away. The sound worked. The video card worked. Even the 8-in-one media card reader worked. CD-writer worked. DVD-writer worked. USB worked.

So I'm playing around with Skype now, which installed flawlessly as a .deb, and I can't get the microphone to work. I've tried using just about every configuration I can think of in Volume Control--even changing from [NVidea nForce2 (Alsa Mixer)](http://i22.photobucket.com/albums/b337/psychocats/5ae8e86b.png) to [Realtek ALC650F (OSS Mixer).](http://i22.photobucket.com/albums/b337/psychocats/c9a993aa.png) 

I did a few searches, but I didn't find anything helpful:

[http://66.102.7.104/search?q=cache:uxL_tRnkhaIJ:ubuntuforums.org/showthread.php%3Ft%3D13603+site:ubuntuforums.org+skype+microphone&hl=en&lr=lang_en](http://66.102.7.104/search?q=cache:uxL_tRnkhaIJ:ubuntuforums.org/showthread.php%3Ft%3D13603+site:ubuntuforums.org+skype+microphone&hl=en&lr=lang_en)
[http://66.102.7.104/search?q=cache:_cS0EWN_9nAJ:ubuntuforums.org/archive/index.php/t-21186.html+site:ubuntuforums.org+skype+microphone&hl=en&lr=lang_en](http://66.102.7.104/search?q=cache:_cS0EWN_9nAJ:ubuntuforums.org/archive/index.php/t-21186.html+site:ubuntuforums.org+skype+microphone&hl=en&lr=lang_en)
[http://66.102.7.104/search?q=cache:WmXG6g4GFLAJ:ubuntuforums.org/showthread.php%3Ft%3D13709+site:ubuntuforums.org+skype+microphone&hl=en&lr=lang_en](http://66.102.7.104/search?q=cache:WmXG6g4GFLAJ:ubuntuforums.org/showthread.php%3Ft%3D13709+site:ubuntuforums.org+skype+microphone&hl=en&lr=lang_en)

Here's the rub: it works perfectly fine in Mepis, so it's not a Windows/Linux thing. I'm wondering whether it's a Gnome/KDE thing or a Ubuntu/Mepis thing or even a Hoary/Breezy thing (I'm using Breezy now).

Any ideas of what I should try or any more details I should give that will help people help me? I'd really like to try out this Skype thing, and I'd hate to have to go back to Mepis (even though it is a great distro).

Thanks in advance...[/QUOTE]

First, are you a beginner?

Second, do you use Ubuntu or Kubuntu? I forgot.

---

### Post by aysiu on 2005-09-08
[QUOTE=poofyhairguy]First, are you a beginner?[/quote] Well, I've been using Linux for four months. I'm not sure...

> 
Second, do you use Ubuntu or Kubuntu? I forgot. I use Ubuntu (Breezy).

---

### Post by chiefofthejojos on 2005-09-08
This might sound stupid but did you make sure the microphone wasn't muted?  It actually took me awhile to notice this in the volume control applet.

---

### Post by poofyhairguy on 2005-09-08
[QUOTE=aysiu]
 I use Ubuntu (Breezy).[/QUOTE]

Thats what I hoped. I'll be very honest with you, seeing how active a member you are (it would suck to lose you). 

You need to file a bugzilla report. Its easier than it looks. Ask here if you have problems. Someone might have never had this set-up in Ubuntu....the developers might not know.

Then if it is not fixed by release...well...you know....

---

### Post by aysiu on 2005-09-08
[QUOTE=poofyhairguy]
You need to file a bugzilla report. Its easier than it looks. Ask here if you have problems. Someone might have never had this set-up in Ubuntu....the developers might not know.[/QUOTE] That's what I was hoping you *wouldn't* say, but it's probably what's most reasonable. I'll probably do a bit more testing, though, to see if it's a Gnome/KDE thing or a Hoary/Breezy thing.

---

### Post by aysiu on 2005-09-08
[QUOTE=chiefofthejojos]This might sound stupid but did you make sure the microphone wasn't muted?  It actually took me awhile to notice this in the volume control applet.[/QUOTE] Yeah, I made sure. You can never assume people have tried stuff like that, though. Thanks for the suggestion.

---

### Post by aysiu on 2005-09-08
Nope.
I tried it in Hoary. Same problem.
Do you think it's worth me sudo apt-get installing kde in Ubuntu just to see if it's a KDE/Gnome issue?
I've tried just about every combination I can think of in the mixer...

---

### Post by poofyhairguy on 2005-09-08
[QUOTE=aysiu]Nope.
I tried it in Hoary. Same problem.
Do you think it's worth me sudo apt-get installing kde in Ubuntu just to see if it's a KDE/Gnome issue?
I've tried just about every combination I can think of in the mixer...[/QUOTE]


If you have the bandwidth, why not? If it works I'll tell you some cool KDE stuff to make it work better with Gnome Apps.

---

### Post by poofyhairguy on 2005-09-08
[QUOTE=poofyhairguy]If you have the bandwidth, why not? If it works I'll tell you some cool KDE stuff to make it work better with Gnome Apps.[/QUOTE]

Edit: do it this way though

> sudo apt-get install kubuntu-desktop

---

### Post by aysiu on 2005-09-08
I'll give it a shot. Thanks, Poofy.

---

### Post by aysiu on 2005-09-08
Okay. It's a KDE v. Gnome thing. It's not a Mepis/Ubuntu thing or a Breezy/Hoary thing.

So I downloaded the Kubuntu desktop, and when I enabled the "capture" part of the mixer (see [screenshot](http://i22.photobucket.com/albums/b337/psychocats/8bda15a3.png)--it's on the far right), it worked.

So what is it in Gnome I have to enable? Or can I use the KDE mixer in Gnome?

Or do I just have to use KDE?

---

### Post by poofyhairguy on 2005-09-08
[QUOTE=aysiu]Okay. It's a KDE v. Gnome thing. It's not a Mepis/Ubuntu thing or a Breezy/Hoary thing.

So I downloaded the Kubuntu desktop, and when I enabled the "capture" part of the mixer (see [screenshot](http://i22.photobucket.com/albums/b337/psychocats/8bda15a3.png)--it's on the far right), it worked.

So what is it in Gnome I have to enable? Or can I use the KDE mixer in Gnome?

Or do I just have to use KDE?[/QUOTE]

Well...hmm...you could try to use arts or whatever the KDE sound thing in Gnome....but I would just use KDE. I'm switching over too for 3.5.

First, there is a how to to make KDE apps look like Gnome apps. Then run:

> gnome-settings-daemon

And Gnome apps won't look like crap in KDE. You can also add the Gnome panels if you want:

> gnome-panel

I know I do- my least favorite thing about KDe is kicker.

I mean, your other option is Mepis right? Might as well use Kubuntu so that you can avoid that whole "Mepis uses stuff from all three version of debian so a dist-upgrade really borks it" thing.

---

### Post by aysiu on 2005-09-08
Yeah, I think I might do that. I have to say I've really grown to love Gnome, but KDE isn't too bad, either. Thanks for your help, Poofy.

I might be turning Kubuntu.
Yeah, Mepis... it's too bloated for me, and the sources.list is patchy...

---

### Post by aysiu on 2005-09-10
Okay. This is weird.

I installed Kubuntu, but, for some reason, the regular repositories didn't work. I kept getting that thing about not being able to "stat" the sources.

So, I gave up for a while.

In the meantime, I've just been using my Breezy (Gnome) partition. Just this morning, I get an update notification (that little red circle in the notification area). I installed the updates, and all of a sudden the microphone worked!

I wonder what got updated.

Did the devs read my mind? Did someone file a bug report for me? Well, whatever happened, it's all cool now. Weird.

---

