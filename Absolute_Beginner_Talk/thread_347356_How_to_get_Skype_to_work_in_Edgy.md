---
title: "How to get Skype to work in Edgy???"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2007-01-27
Hi
Recently upgraded to Edgy and installed newest version of Skype (1.3.0.53 API) at the same time.
However, while I previously had problems running Skype in Dapper (earlier version of Skype) at least it was occasionally possible to make SkypeOut calls.

However, now, I can neither call PC-to-PC nor PC-to-Phone using Skype in Ubuntu.

If I try PC-to-Phone, the call starts as normal but after perhaps 1-2 rings it stops and a "Call Failed" message appears.

For PC-to-PC, although the receiving PC can see that I am calling, a "Problem with Sound device" message appears and neither of the two PCs can hear anything.

My machine is multiboot and Skype works absolutely perfectly in all modes when I'm in WinXP confirming that the sound device problem is not a hardware issue.

I have removed and reinstalled Skype several times but always with the same result.

I would like to know if Skype actually works well  (including PC-to-Phone) in Edgy for anybody and if so what can you recommend that I do to overcome this annoying problem.

Thanks
Paul

---

### Post by jazzuban on 2007-01-27
Skype works fine for me on Edgy (installed through Automatix2).

---

### Post by Xappe on 2007-01-27
make sure skype uses alsa and not oss.

---

### Post by PaulFXH on 2007-01-27
Thanks for the replies.

jazzuban
When you say "works fine", are you also including SkypeOut calls i.e. PC-to Phone?
If so, did you have to do anything special or it just worked straight out of the box?

Xappe
This seems to be addressing my second problem where PC-to-PC calls are impossible because of an undefined sound device problem.
How do you do that to change from Alsa to Oss for Skype?
I had already played around with System>Preferences>Sound to change from Alsa to Oss (and others) but none improved my Skype situation.

I saw another thread here recently claiming to have solved the Skype problem by switching to Gizmo (perhaps a touch of irony here!)..
However, Gizmo doesn't work for me as I get an error on login complaining of  no audio capture device detected.
Unfortunately, even though this is probably the source of my Skype (PC-to-PC) problem as well, I can't see how to rectify this.

Whatever about this problem, I just do not see any light at the end of the tunnel for the PC-to-Phone difficulty despite the affirmation from jazzuban.

I need help badly.

---

### Post by Xappe on 2007-01-27
you should be able to change sound devices in the skype options...
(Tools -> Options -> Sound devices)

---

### Post by Tomosaur on 2007-01-27
In your above post, you seem to have confused what Xappe suggested. You need to make Skype _use Alsa_, and **not** oss.

Skype (and SkypOut) worked fine for me right out of the box. I did need to set Skype to use my Skype phone rather than the microphone, but I've had no troubles whatsoever.

So, go through all of the Skype configuration menus, and change all references of OSS to Alsa. OSS does not work for me, either.

---

### Post by PaulFXH on 2007-01-27
Thanks for the further replies.

This time things are looking an awful lot better.

Just to clarify, I did actually follow EXACTLY what xappe said and changed the Sound Device to OSS rather than Alsa and amazingly that seems to have solved BOTH of my problems.

So, now I can call PC-to-PC and PC-to-Phone exactly as I can on WinXP (except there's no video or call recording but that's a minor inconvenience).

So, very many thanks to xappe for that great suggestion.

Nevertheless, there's still just one problem that hasn't gone away. When I shut down Skype and then come back to it, it refuses to start up saying that there is another instance of Skype running. And indeed there always is which I have to Kill before attempting to open Skype again.
After killing it, it works fine after starting up again.
Why won't it shut down completely?

---

### Post by RichPicker on 2007-02-08
HOLY COW!! Here's what Skype support has to say about it. If anyone can guide me through this, I would really appreciate it.

On linux you should verify the Capture leveler on the sound control and 
also ensure your mic and capture device are set to capture/record in 
your mixer program. 
---------------------------------------------------------------------------------------------------------------------------------
I also advise you to visit Ubuntu forum 
[http://ubuntuforums.org/showthread.php?t=214273](http://ubuntuforums.org/showthread.php?t=214273).

There are still some audio problems (for some users, especially those 
on Ubuntu 6.06), and we will try to address them in further versions.

For Ubuntu 6.06 users - upgrade to 6.10, it will fix most of your audio 
problems

In order for Linux to recognize and use your soundcard, you have to 
load the appropriate driver. As of the 2.6 version of the kernel, that 
means enabling the ALSA (Advanced Linux Sound Architecture) driver for you 
card. Take a look at the ALSA Soundcard Matrix to determine which 
driver you are supposed to use for your speciffic card.

Now, you will have to modify your /etc/modules.conf or 
/etc/modules.d/alsa (check your distribution for details on the correct way to load and 
configure modules) and add the following:
Code:

# This sets up the ALSA and OSS portion
alias char-major-116 snd
alias char-major-14 soundcore

# Replace "driver" with the driver for you soundcard
alias snd-card-0 snd-driver
alias sound-slot-0 snd-card-0

# Configure the OSS emulation layer
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

alias /dev/mixer snd-mixer-oss
alias /dev/dsp snd-pcm-oss
alias /dev/midi snd-seq-oss

# If you have more than 1 card, set this number to the correct value
options snd cards_limit=1
options snd-pcm-oss nonblock_open=1

Note that a lot of this configuration is dedicated to something called 
OSS (Open Sound System) emulation. This mimics the behaviour of the old 
Linux sound system so as to be backward compatible with older software 
that does not yet support the new sound system. One such piece of 
software is Skype - so it is important that it is running and configured 
correctly.

Now, it is time to load the drivers. How you do that depends on your 
distribution - you may have an /etc/init.d/alsa or similar script that 
will do it for you. If you are unable to figure it out, a reboot will do 
it

---

### Post by ^rooker on 2007-02-08
@PaulFXH: 
You **are** aware of the fact that Skype's using a super-secret and evil proprietary protocol, right?

Which is something that should be avoided to use and spread - if possible, right?
(sorry, but couldn't keep my mouth shut about that)

---

### Post by MichaelSM on 2007-05-08
To PaulFXH. Every time you load up Skype, a yellow/orange (I'm colour-blind) icon appears in your panel. In my case I have the panel at top of screen, and next to the loudspeaker symbol is where the Skype icon appears when loaded. This is different from the blue Skype launcher on the other side. To exit from Skype, you have to right-click on the first one I mentioned, then click 'Close.' 
Not to lead you up the garden path, regarding the blue Skype icon I mentioned; maybe you access Skype as in Applications>Internet>Skype and possible have not right-clicked on Skype and  added it to your Launch panel. Doesn't really matter. When you start Skype, look for the appearance of a coloured icon in your panel. That's the one you use to close it completely, not the X in the Skype window.
Mike.

---

### Post by PaulFXH on 2007-05-08
@MichaelSM
Thanks for the tip.
Unfortunately, I'm a very long way from my Linux box right now, so I can't check what you suggested. However, I really don't remember any yellow/orange icon.
Nevertheless, I'm going to try this out when I get back.
Best wishes
Paul

---

### Post by wieman01 on 2007-05-08
> **^rooker said:**
> @PaulFXH: 
You **are** aware of the fact that Skype's using a super-secret and evil proprietary protocol, right?

Which is something that should be avoided to use and spread - if possible, right?
(sorry, but couldn't keep my mouth shut about that)
If you can tell me how I can possibly avoid SKYPE and use a similar tool that is just as easy to set up (no port forwarding, etc.), I am all ears. Sadly SKYPE is the best option when it comes to ease of installing and support. EKIGA is not option at all... Don't get me going here. ;-)

---

### Post by robertpolson on 2007-05-09
Gizmo project ?

---

### Post by kvonb on 2007-05-09
[http://www.openwengo.com/](http://www.openwengo.com/)

Some people have had problems with the audio in the past, but I had it working under Edgy, I haven't tried the latest version under Feisty though.

PS.  My wife uses Skype a lot, and she reports that it works better under Ubuntu than Windows, she says it is much clearer!

---

