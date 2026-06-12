---
title: "Want more volume?  Max not enough."
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2008-02-03
I'm using an SB Live! audio card.

Typing "alsamixer" in the Konsole - it's turned up all the way, or it was turned up all the way - I just checked it and got this error msg: "*alsamixer: function snd_ctl_open failed for default: No such device*" - but last time I checked (and I've been having this problem awhile) it was turned up all the way - the correct sound card is selected in the "sound preferences" - yet when I turn it up all the way - it's BARELY dealable.  On windows I only had to use like 2/5 volume with my headphones on for it to be enough - with this I need full and that's BARELY enough.

How can I amp the sound?

I switched to my onboard soundcard which had a higher volume but it had a ****-ton of interference (not a fair trade IMO).  I know it's NOT the sound card's ability is being maxed out simply b/c when using it in Windows I can put it at like 2/5 and be fine.

Any help?  The max just isn't high enough...at all... :(

EDIT:
PS:  Is it possible the SB Live! needs drivers that need to be installed?

---

### Post by toddward on 2008-02-04
Play with your PCM Volume settings...careful though not to crank it up too fast.

---

### Post by Syndacate on 2008-02-05
Where are they?

---

### Post by (((X))) on 2008-02-05
at the terminal
$ alsamixer
There is PCM somewhere in that window

---

### Post by monte48lowes on 2008-02-05
Quick question. With the SB Live! do you also have an onboard sound card? I do, and I had to disbale the onboard sound in the BIOS to get kmix and alsa to detect the correct card everytime.

Mike

---

### Post by Syndacate on 2008-02-06
> **monte48lowes said:**
> Quick question. With the SB Live! do you also have an onboard sound card? I do, and I had to disbale the onboard sound in the BIOS to get kmix and alsa to detect the correct card everytime.

Mike

I do have an onboard soundcard, and yes, it's disabled in the BIOS.  It detects the correct card - I have sound, just not enough of it..

as far as typing "alsamixer" - I keep pulling this error msg - which is new ****, it didn't used to do this, it used to come up fine (but was up all the way).

```

$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```

:(

---

### Post by Syndacate on 2008-02-06
*bump* - anybody?  This si the one thing I've never been able to get to work in Ubuntu - speakers/headphones only need like 1/4 vol in Windows - so I know the card's not topped or anything.

---

### Post by Syndacate on 2008-02-07
?

---

### Post by Syndacate on 2008-02-15
Blah?  Anybody?  This volume maxing out so early is killing me :(.

---

### Post by Syndacate on 2008-02-16
**sniffle sniffle

---

### Post by paydaydaddy on 2008-02-16
Have you tried uninstalling/re-installing alsamixer? I suggest using synaptic to re-install. The comprehensive sound tutorial has helped me in the past.
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by sloggerkhan on 2008-02-16
Yeah, you need alsa mixer to work.
It should open up if you right click on the volume applet slider and hit open volume control.
But unfortunately you have a problem with.

---

### Post by Syndacate on 2008-02-17
> **sloggerkhan said:**
> Yeah, you need alsa mixer to work.
It should open up if you right click on the volume applet slider and hit open volume control.
But unfortunately you have a problem with.

That part works fine - if I change the volume or edit the preferences.

I do indeed get sound - though if I hit any of the "test" buttons it gives me a failure msg (nothing useful mentioned), and if I type "alsamixer" in the command line it gives me a failure msg (again, nothing useful)

I went to synaptic and installed everything that started with "alsa" - no change.

I couldn't uninstall alsamixer - don't know what it's "officially" called - but I uninstalled/reinstalled alsa-base and that had no effect as well :(

Volume applet slider in the top right works - all the properties work - and I can turn it up all the way - and like I said before, sometimes that's BARELY enough :(.

---

### Post by Sinkingships7 on 2008-02-17
double click the volume applet and go to edit -> preferences.

you'll want PCM, Front, Surround, & Center all on (if given the option. i do, because i'm using 6 channel audio). make sure all of the are all the way up. especially if you're using a surround sound system with more than 2 channels.

---

### Post by expatCM on 2008-02-17
One of the Linux distros was said to be very good for sound diagnostics ...  just boot the Live CD.

Of course I cannot remember which it is.  I think it is dynebolic
[http://dynebolic.org/](http://dynebolic.org/)

---

### Post by Redptc on 2008-02-17
Hello Syndacate, I found that sound can be a real pain in gutsy! Mine is an on-again/off-again sort of problem. It's been a thorn ever since I started with Ubuntu!

Can I ask a  question about your sound; do you get all the sounds only very quiet? 

I mean, do you get the login warning drum, login successful and all the boinks and things. What about logout! Do you get sound out Firefox or similar?

---

### Post by Syndacate on 2008-02-20
> **Redptc said:**
> Hello Syndacate, I found that sound can be a real pain in gutsy! Mine is an on-again/off-again sort of problem. It's been a thorn ever since I started with Ubuntu!

Can I ask a  question about your sound; do you get all the sounds only very quiet? 

I mean, do you get the login warning drum, login successful and all the boinks and things. What about logout! Do you get sound out Firefox or similar?

Yeah, all the sound works where it's supposed to, the maximum volume is just pathetically low.  Back when alsamixer worked all the volumes were turned up all the way in there, too.

I don't see getting a whole different linux distro just to get more volume, but this is really just annoying me, not really killing me.

---

