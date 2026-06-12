---
title: "Anyone use Goldwave audio editor with ubuntu?"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by discmaster on 2007-06-04
I have used Goldwave for years with windows. I tried to install it under wine, but no go for me. Has anyone had any success with using goldwave with linux/ubuntu?

---

### Post by animusFL on 2007-06-04
> **discmaster said:**
> I have used Goldwave for years with windows. I tried to install it under wine, but no go for me. Has anyone had any success with using goldwave with linux/ubuntu?

 discmaster, 
    I used goldwave waaaay back in my windoze days, here's a page with some of the 
 wav editors for linux.... [http://www.linuxjournal.com/article/7274](http://www.linuxjournal.com/article/7274)   
   hope this helps
    animusFL

---

### Post by discmaster on 2007-06-04
Hi animusFL,

Thanks for the link, I am off to read that now; In the meantime, I did get goldwave installed with wine, & it will open, however that is as far as I can go.

It will not load a file, or if I try to record a file playing over the sound card, it says driver not found or some such nonsense!

I will keep trying...

---

### Post by discmaster on 2007-06-04
Still no good - "sound driver does not support the current sample rate or is missing a plugin"...

Any suggestions?!?!

---

### Post by animusFL on 2007-06-04
> **discmaster said:**
> Still no good - "sound driver does not support the current sample rate or is missing a plugin"...

Any suggestions?!?!

No idea here, haven't tried wine ( I use vmware and a virtual windoze when I need it )
 not sure if you can get goldwave working that way... Anyone else on this?? You may just
have to bite the bullet & try one of the linux apps for wav editing... good luck with the
learning curve & finding one that suits your needs.
   animusFL

---

### Post by XxTaylorxLovelyxX on 2007-06-04
Ubuntu sucks

---

### Post by discmaster on 2007-06-04
:( 

I am beating just about everything to death trying to get any audio editor working with ubuntu. Audacity would be ok, but all I get with it is distorted/scratchy recordings.

I did start another thread asking what audio editors others use, but so far, no one has posted.

I did get goldwave configured with wine & it will open & load a file, but i can't playback.

> "sound driver does not support the current sample rate or is missing a plugin"

---

### Post by ramjet_1953 on 2007-06-04
You will find that Audacity will be fine, if you do the following:

1. Make sure that [COLOR="Blue"]alsa-oss[/COLOR] is installed. Check this out, using Synaptic package manager.

2. As Audacity is OSS based, you need to start it with the command:

[COLOR="Red"]aoss audacity[/COLOR]

You can change the startup command in the menu, by using [COLOR="Blue"]System>Preferences>Main Menu[/COLOR] and editing the startup command for Audacity.

Regards,
Roger :cool:

---

### Post by discmaster on 2007-06-04
Hi ramjet,

I posted a follow up in the other thread that you referenced this; I did exactly as you outlined, & it didn't seem to work for me...

I double-checked all the settings, & still no good...

---

