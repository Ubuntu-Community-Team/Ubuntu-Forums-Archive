---
title: "Audio i/o layer problem: No mic?"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by Forcestar on 2008-04-01
I appear to have a microphone error... I'm using a Dell Latitude C610. Whenever I try to use Audacity, I get the following message: There was an error initializing the audio i/o layer. You will not be able to play or record audio.

Not only that, but my microphone won't work with other applications. I've tried Skype, and while I can hear I can't be heard (yes, my microphone is working, tested it on another computer). I can play music via Rythmnbox or similar, simply not record. Any suggestions?

---

### Post by BandD on 2008-04-01
Could you post the output of the below run in a terminal:

```
lspci | grep Audio
```

Also, are you plugging your mic into a mic jack on your computer or USB or something else?

Thanks,

Dustin

---

### Post by gunjin1 on 2008-04-02
Similar problem on a Dell D620. My output looks like this:
> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

I can hear audio in the headphones but nothing is picked up on my mic. 

3rd week with Ubuntu so total newbie here. Any recommended solutions would help me out as well:)

---

### Post by _aXXe_ on 2008-04-02
> **gunjin1 said:**
> Similar problem on a Dell D620. My output looks like this:


I can hear audio in the headphones but nothing is picked up on my mic. 

3rd week with Ubuntu so total newbie here. Any recommended solutions would help me out as well:)

Try this. It's designed for laptops with Intel hda sound cards but it worked on my desktop. with an Intel cpu and a realtek alc662 -rev 1 sound card.

Read the entire article before you start installing anything.

[http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html](http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html)

---

### Post by Forcestar on 2008-04-02
I get this output...

> 0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)

---

### Post by Forcestar on 2008-04-02
OK, tried the anthonywilliams-blog link, the 2nd part of the script couldn't put the file where it was supposed to go (no directory). Now I have no sound whatsoever.

Some please help?

---

### Post by BandD on 2008-04-02
Yeah, that script isn't going to work with your sound card.  That link was meant for gunjin1 I think.  The first part should be fine, it jsut updates ALSA to the most current version (though sometimes that will break your sound).

Your sound card is the Intel AC '97, so you'll have to change somethings in the second script.  But I'm not really an expert here, so I can't really give 100% garunteed advice.

Could you post the output of the below run in a terminal:

```
ls /lib/modules/2.6.22-*/kernel/sound/pci/ac*
```

EDIT:

Actually you'll have to change one thing in the first script there as well.  So now things are a little bit more complicated.  Try searching for removing and re-installing ASLA.  Search also for configuring ALSA with an Intel AC97 card.  That's what you'll need to do.

---

### Post by Forcestar on 2008-04-03
I kinda figured the script wasn't meant for me, after the script broke me sound :P Took me about two hours, but removing the -configure flag to install for hda soundcards 'n running it again got my sound back. Unfortunately, it still won't let me use a mic. 

I'm using Dapper, so I had to change your command to the 2.6.15 kernel, but here's what I get:

> /lib/modules/2.6.15-26-386/kernel/sound/pci/ac97:
snd-ac97-bus.ko  snd-ac97-codec.ko  snd-ak4531-codec.ko

/lib/modules/2.6.15-51-386/kernel/sound/pci/ac97:
snd-ac97-codec.ko  snd-ak4531-codec.ko


---

### Post by BandD on 2008-04-03
Just out of curiosity could you post the output of:

```
ls /lib/modules/2.6.15-26-386/ubuntu/media/
```

You're obviously working with a different kernel than me, so I'm not 100% sure if ALSA interacts with the kernel differently.  I would guess not.  But anyway, if you can make sense of this site (it's a little confusing, but basically it lists all the module options for the ALSA driver) :

[http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt")

do a FIND in your web browser for AC'97 and you'll find some info there.  It looks like it wants you to configure ALSA with the snd-intel8x0 module, but I'm not really certain.  I'll try to look into it a little more tomorrow.

---

### Post by Forcestar on 2008-04-03
Oddly enough, I get...

> ls: /lib/modules/2.6.15-26-386/ubuntu/media/: No such file or directory

Maybe it has to do with me running dapper?

---

### Post by BandD on 2008-04-03
It might, I only started using Ubuntu with Gutsy, so I'm afraid I can't be of too much help.  

Still, try searching for ways to configure ALSA with the intel AC'97 chipset.  That will be the key.

Hardy should be out in the next three weeks or so and there's a good chance your mic might work out of the box with that, if you are planning on upgrading.

---

### Post by Forcestar on 2008-04-03
I'll get on working with ALSA... I just hope me the newb can figure it :P

And this computer is an ooooold box, I couldn't even run the Feisty Live CD at a reasonable speed. I think Hardy is just a tiny bit out of my reach ;)

---

### Post by gunjin1 on 2008-04-04
> **BandD said:**
> Yeah, that script isn't going to work with your sound card.  That link was meant for gunjin1 I think. 

Thanks for the reply. Been busy at work so will give it a shot this weekend! :)

---

