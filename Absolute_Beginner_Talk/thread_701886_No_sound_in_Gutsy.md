---
title: "No sound in Gutsy"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by ObsessedMikey on 2008-02-19
Hi guys, I'm a brand new user to Ubuntu and I've just installed Ubuntu Gutsy (as recommended by a friend) on my laptop.  I've managed to get Wi-Fi running quickly and easily, and get myself the full lot of updates available, so now I'm running a fully up-to-date version of Gutsy.

However, I do not have any sound what so ever, and I've tried plugging something into the headphone port and still no sound.  I'm not sure quite what the problem is, as I'm dual-booting with Vista and Vista has no problems what so ever with my sound.  

My laptop is a HP Compaq Presario V6560EA
and my sound chip is a Realtek 268.

Any help would be greatly appreciated, but I do ask please that you give me very basic instructions as I do not currently know anything about Ubuntu or Linux.

Thanks again, and thanks for your time. :)

---

### Post by timbounceback on 2008-02-19
System->Administration->Restricted Drivers Manager; then see if there's anything there

---

### Post by teamkiller87 on 2008-02-19
You should take a look at this how-to... I had issues with a Realtek sound card when I first installed Ubuntu but this helped me fix it.

[https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28sound%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28sound%29)

Oh, and it's pretty straightforward as well...

---

### Post by benfindlay on 2008-02-19
Ok, this might seem really daft, but lets just eliminate it as this was my problem with my old dell laptop:

Try double clicking on the volume icon next to the clock and choosing Edit>Preferences. If either Master or Master Mono are unticked, tick them. Then it's liekly that the unticked channel is muted or turned down. Just unmute and turn up and you should be good to go!

Hope this helps!

---

### Post by ObsessedMikey on 2008-02-19
Hi, thank you both for your help.

Firstly, timbounceback, I've just looked and theres only my wireless driver in there :(

Secondly, teamkiller87, I did have a look at that before, but to be honest I was a bit baffled when it came to updating the ALSA or whatever it is, I didn't quite understand how to do it very easily.

---

### Post by ObsessedMikey on 2008-02-19
> **benfindlay said:**
> Ok, this might seem really daft, but lets just eliminate it as this was my problem with my old dell laptop:

Try double clicking on the volume icon next to the clock and choosing Edit>Preferences. If either Master or Master Mono are unticked, tick them. Then it's liekly that the unticked channel is muted or turned down. Just unmute and turn up and you should be good to go!

Hope this helps!

Sadly I've just checked and they were already ticked :( Thanks all the same though!

---

### Post by teamkiller87 on 2008-02-19
Okay, then I'll just post exactly the code which worked for me...

First, open the file /etc/modprobe.d/alsa-base with a text editor. The simplest way is to run this in a terminal: 

sudo gedit /etc/modprobe.d/alsa-base

And then, go to the end of the file and add the following line:

options snd-hda-intel model=auto


Hope this helps!

---

### Post by om1 on 2008-02-19
to find out what your model number is look under the laptop and you will see a white sticker and it will say warranty on the bottome of it... above it it will say your model number dv6XXX

---

### Post by ObsessedMikey on 2008-02-19
> **teamkiller87 said:**
> Okay, then I'll just post exactly the code which worked for me...

First, open the file /etc/modprobe.d/alsa-base with a text editor. The simplest way is to run this in a terminal: 

sudo gedit /etc/modprobe.d/alsa-base

And then, go to the end of the file and add the following line:

options snd-hda-intel model=auto


Hope this helps!

Thanks, I did exactly that, but do I have to do something after? Or is it meant to suddenly just work? Cause the sound isn't working :(


Thanks om1, it's a V6560EA, I've edited my original post accordingly.

---

### Post by teamkiller87 on 2008-02-19
Oh yeah, sorry... You should reboot after that...

---

### Post by ObsessedMikey on 2008-02-19
> **teamkiller87 said:**
> Oh yeah, sorry... You should reboot after that...

I did actually :P to no avail :( still no sound...

---

### Post by Hobo Joe on 2008-02-19
Paste the output of:
```

sudo asoundconf list

```

---

### Post by ObsessedMikey on 2008-02-19
Hi again, I did as you said and the following came up:

> Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
Intel


---

### Post by Hobo Joe on 2008-02-19
Run this command:

```

sudo asoundconf set-default-card Intel

```

That SHOULD fix it.

---

### Post by om1 on 2008-02-19
looked up your laptop with the model number and it says your sound card is 
3D Sound Blaster Pro compatible sound 16 bit integrated

here is the link to it
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01114276&lc=en&cc=us&dlc=en&product=3466340&rule=46381&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01114276&lc=en&cc=us&dlc=en&product=3466340&rule=46381&lang=en)

---

### Post by ObsessedMikey on 2008-02-20
> **Hobo Joe said:**
> Run this command:

```

sudo asoundconf set-default-card Intel

```

That SHOULD fix it.

Nope...still no sound I'm afraid.  :(  Thanks for the help though.

[QUOTE=om1]looked up your laptop with the model number and it says your sound card is
3D Sound Blaster Pro compatible sound 16 bit integrated

here is the link to it
[http://h10025.www1.hp.com/ewfrf/wc/d...=46381&lang=en](http://h10025.www1.hp.com/ewfrf/wc/d...=46381&lang=en)[/QUOTE]

Hmm...That's just weird lol, cause even in Vista the laptop came bundled with Realtek 268 drivers...:confused: What do you think I should do?

---

