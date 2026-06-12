---
title: "xmms - no more sound"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by Corvair on 2006-07-12
Hello everyone,

I tried to install lastfm player. For that I needed to install audioscrobbler for xmms which I did, with the plugin in xmms.
Following this, the lastfm player does not work and mostly my xmms does not give out any sound although it is working.

How can I find out what I did wrong and get sound back out of XMMS?

---

### Post by Kapre on 2006-07-12
> **Corvair said:**
> Hello everyone,

I tried to install lastfm player. For that I needed to install audioscrobbler for xmms which I did, with the plugin in xmms.
Following this, the lastfm player does not work and mostly my xmms does not give out any sound although it is working.

How can I find out what I did wrong and get sound back out of XMMS?

Corvair - try checking your sound settings. Try to changing it to ALSA or Esound. 

K

---

### Post by Corvair on 2006-07-12
I forgot to mention that my card is working fine (via82c868a/b). I have sound  when I use Rithmbox and Movie Player. Also XMMS is working because I can see the signal on the window viewer but it is like it was muted, no sound is commimg out. I have deactivated Audioscrobbler and taken out the plugin out of XMMS. It remains muted for some reason.

---

### Post by Perfect Storm on 2006-07-12
Is it all your music on xmms or just when you play your CDs?
If so change CD audio Plugin from analog to digital.

---

### Post by chickengirl on 2006-07-12
[quote=Corvair]I forgot to mention that my card is working fine (via82c868a/b). I have sound when I use Rithmbox and Movie Player. Also XMMS is working because I can see the signal on the window viewer but it is like it was muted, no sound is commimg out. I have deactivated Audioscrobbler and taken out the plugin out of XMMS. It remains muted for some reason.[/quote]

Open up XMMS preferences (right click almost anywhere on XMMS' chrome > options > preferences), go to the "Audio I/O Plugins" tab and switch the output plugin to ALSA or esound.

---

### Post by Corvair on 2006-07-12
This happêns on all music, from file and from cd.
I tried changing from analog to digital and there is no difference.

I tried swithcing from alsa to esound and there is no difference either.

xmms is displaying as usual as if it is playing but no sound is comming out.

Real mind bogling.

Thanks for the efforts so far

---

### Post by Corvair on 2006-07-14
Hello everyone,
I went to the below mentionned thread to try to solve my xmms sound problem, by deleting my alsa sound driver and reintaling the driver. I am not sure yet if this has solved the problem because I cannot enter my Ubuntu operating system. 
I had to reboot as per request after the above change. When I reboot I come up with a black screen and a request for name and password for logging in. 
All I get is this:  claude@ubuntuclaude:~$
and I cannot get out of this.

Of course, I forgot to tell you, I am a newby at this :mrgreen: 

I am sending this message from windows, as I cannot open Ununtu.

Help!!!




Getting Alfa drivers from fresh kernel.

[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=alsa+configuration](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=alsa+configuration)

---

### Post by Paerez on 2006-07-14
just an update, we solved corvair's ubuntu desktop problems, but the xmms no-sound problem still exists. Now for my suggestion:

1) OK this is a just a quick check. Is your XMMS volume turned up? The volume slider is not labeled and this confused me a lot the first time I used XMMS. See the attached picture.

2) Try switching to the alsa driver, then clicking configure and manually selecting your device.

3) Open gnome's volume control and make sure the sliders are up for PCM, Master, and any others you think might work.

---

### Post by Corvair on 2006-07-14
Hello again,

The volumes are ok.
I have sound on Rythmbox and Movie player and everywhere else.

Here are the settings for the output plugin:

Alsa: 1.2.10 output plugin
Device settings:
Audio device: Default (default PCM)
Miser card: Via 82c868a/b rev20
Mixer device: master

---

### Post by Perfect Storm on 2006-07-15
Have you tried with BMP or Audacious? They are clones of Xmms.

---

### Post by Corvair on 2006-07-15
BMP will not play either.
It says to check sound card and make sure it is set up properly.

I don't have Audatious or do you mean Audacity? If so I don't have it

---

### Post by Corvair on 2006-07-15
Hello Artificial Intelligence,
I just installed Audacity.
I got this message after installing: Error initializing audio
Audio i/o layer. You will not be able to play or record audio. (Host Error)

I tried to play a file and I got this message: Error trying to play:
Error while opening sound device. Please check the output device settings and the project sample rate.

There is something wrong with my sound card configuration.
How do I open the file to correct it?

---

### Post by Corvair on 2006-07-15
delete this message

---

### Post by Perfect Storm on 2006-07-15
No, Audacious (though it's not in the repo, but needs compiling).
But if other sound/music player won't play either it looks like a sound card problem or sound driver problem.

---

### Post by Corvair on 2006-07-15
How do I get to my sound driver to modify it?

---

### Post by Corvair on 2006-07-15
If this can help clarify the problem.....

Under device manager I have listed twice:
VT82xxxxx UHCI USB 1.1 Controler.

Under Advance I have :
pci.subsys_vendor   strlist    VIA Technologies, Inc. (Wrong ID)

---

### Post by Perfect Storm on 2006-07-15
Sorry, I can't help you there. Perhaps another member can / who might have the same chip.

---

### Post by Corvair on 2006-07-24
Hello everyone,

Finely my XMMS is giving out SOUND again.

My mistake: I had enabled voice enable plugin in the effects plugins menu.

Options--> preferences--> effects plugins--> voice removal plugin-->disable
That fixed the problem.

Thanks to everyone who was in on this.

:-D

---

### Post by LinuxLemur on 2006-07-27
Once again, a post already existed that helped me fix my problem.  Thanks Artificial Intelligence, the CD audio plugin somehow got put on analog.  Probably when messing around with AMOROK that I didn't get to work.  That's OK I like XMMS just fine so far!

---

