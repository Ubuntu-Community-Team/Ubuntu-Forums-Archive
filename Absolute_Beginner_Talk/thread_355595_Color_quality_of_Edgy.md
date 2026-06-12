---
title: "Color quality of Edgy?"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by headlice on 2007-02-07
Could someone please tell me the color quality of Edgy?  It seems like it is 16 bit.  I would prefer 32, but 24 would be fine.

---

### Post by SunnyRabbiera on 2007-02-07
It should be 32bit as I am running top dollar here.
maybe you should use dapper instead as dapper is often more stable.
now as for the bootscreens, yeh sometimes it is 16 bit or lower but thats because the bootloader on any linux distro is mainly targeted at older PC's.
what kind of monitor do you have?

---

### Post by headlice on 2007-02-07
Well, not sure on my monitor (not at my desktop now) but it is about 3-4 years old.

It has no problems displaying windows at 1020x800 (whatever that resolution is...if I got the #s wrong) and 32 bit.

It just seems like edgy is so fuzzy, like it is running in 16bit color quality.

You said it is standard to run in 32 bit color?

Could you please lead me to where I can select the color quality or possibly some terminal commands?

I have looked everywhere.....

I guess it could be possible that my display driver is not working right.  I have a Geforce4 MX 440, but I thought the updates Edgy does when it connects to the net updates these drivers.

Let me know if I am wrong/misled....

I am not talking about the boot screen either.....I am talking about the desktop view.

---

### Post by SunnyRabbiera on 2007-02-07
the geforce might be giving you issues, remember it is proprietary hardware and sometimes some drivers will not go well with linux.
But your monitor might give you issues too as some monitors are not good on linux either.
this is not linuxes fault mind you as most hardware and software is targeted at windows.
remember that linux is not intended to replace windows, it is a windows alternitive.

---

### Post by headlice on 2007-02-07
I realize that it is an alternative.

I guess I would have never known that a 32bit color display can look like a 16bit color display on the same exact system where a 32bit color display looks like a 32bit color display.....

---

### Post by SunnyRabbiera on 2007-02-07
It could be many factors...
It could be your monitor, sometimes certain monitors will not work or not work good under linux.
Me I have three monitors, my HP monitor works with linux, my dell monitor (somewhat) works with linux, but my gateway forget it...
the geforce might be an issue as well, as linux sometimes doesnt do well with it.
what kind of computer do you have?
this is another factor I must ask you.

---

### Post by irish_flu on 2007-02-07
search for threads which talk about editing the xorg config file (assuming you use gnome).  There's a section in the file for display settings, and color depth is one of these settings (it also controls the options available in Preferences/Screen Resolution).

You should be able to figure out what color depth you're using that way, and play with changing the settings if indeed the color depth is set too low for you.

---

### Post by headlice on 2007-02-07
> **SunnyRabbiera said:**
> It could be many factors...
It could be your monitor, sometimes certain monitors will not work or not work good under linux.
Me I have three monitors, my HP monitor works with linux, my dell monitor (somewhat) works with linux, but my gateway forget it...
the geforce might be an issue as well, as linux sometimes doesnt do well with it.
what kind of computer do you have?
this is another factor I must ask you.

P4 2.6GHz, 1 GB RAM, 80 GB HD, Nvidia Geforce4 MX 440 graphics.  It is a dell, also came with a dell LCD monitor (the one I am running Ubuntu Edgy on)

---

### Post by headlice on 2007-02-07
> **irish_flu said:**
> search for threads which talk about editing the xorg config file (assuming you use gnome).  There's a section in the file for display settings, and color depth is one of these settings (it also controls the options available in Preferences/Screen Resolution).

You should be able to figure out what color depth you're using that way, and play with changing the settings if indeed the color depth is set too low for you.

I already found that help, checked it out, color depth default was set at 24.  I did not see anywhere where it said you could put 32 in there...

I also added commands to enable GLX (open GL?)

Still nothing

---

### Post by SunnyRabbiera on 2007-02-07
ah hah.
Yeh ubuntu might have issues with your LCD monitor, dell is very shaky with linux.
If possible I would suggest you use a different monitor with using linux.
Like I said this kind of stuff is not an issue with linux, it is with hardware developers and trust me dell is one of the worst.
Dell to me hands down has to be the worst computer company out there, even compaq was better to me... that tells you a lot.

---

### Post by headlice on 2007-02-07
> **SunnyRabbiera said:**
> ah hah.
Yeh ubuntu might have issues with your LCD monitor, dell is very shaky with linux.
If possible I would suggest you use a different monitor with using linux.
Like I said this kind of stuff is not an issue with linux, it is with hardware developers and trust me dell is one of the worst.
Dell to me hands down has to be the worst computer company out there, even compaq was better to me... that tells you a lot.

Come to think of it, I did put 6.06 Ubuntu onto a P3 PC one time and it had a big clunky monitor, and if I remember correctly- it looked better than what I have........

It could quite possibly be the monitor......

I just dont understand the difference between the 2 color displays.  It baffles me.....

---

### Post by SunnyRabbiera on 2007-02-07
well you could easily try dapper again, who knows it might work better for you.
Edgy is called edgy for a reason :D

---

### Post by muguwmp67 on 2007-02-07
Correct me if I'm wrong, but my understanding has been  that 24-bit and 32-bit refer to the same thing.

From: [URL="http://en.wikipedia.org/wiki/Color_depth"]
Color depth[/URL]

32-bit color

"32-bit color" is a misnomer when regarding display color depth. A common misconception is that 32-bit color produces 4,294,967,296 distinct colors.

In reality, 32-bit color actually refers to 24-bit color (Truecolor) with an additional 8 bits either as empty padding space or to represent an alpha channel. Considering red, green, and blue use the same amount of bits for their respective color (with the exception of 16-bit color), the total bits used will be a multiple of 3: like 15-bit color (5 bits each) and 24-bit color (8 bits each). The reason for using empty space is that all but the newest modern computers process data internally in units of 32 bits; as such, using this amount for each pixel can allow optimizations.

---

### Post by Sunflower1970 on 2007-02-07
> **SunnyRabbiera said:**
> ah hah.
Yeh ubuntu might have issues with your LCD monitor, dell is very shaky with linux.
If possible I would suggest you use a different monitor with using linux.
Like I said this kind of stuff is not an issue with linux, it is with hardware developers and trust me dell is one of the worst.
Dell to me hands down has to be the worst computer company out there, even compaq was better to me... that tells you a lot.
...Really? I have two computers using Dell LCD 17" monitors, (one's a Dell Dimension 8200, and the other a Compaq Presario 5630) and both work very well with Ubuntu. Both have nVidia cards, one a 7600GT and the other a GeForce3 Ti 500. I downloaded the nVidia drivers with Automatix, then went into my Xorg.conf file and added in "1280x1024" for the resolution. The newer computer and monitor of the two I have I can use the digital input, the older one is the analog input, but you can't tell which is which. Both give me a crystal clear picture. :)

ETA: muguwmp67 that's what I understand, too 32-bit & 24-bit refer to the same thing

---

### Post by Daergeth on 2007-02-07
> **headlice said:**
> I already found that help, checked it out, color depth default was set at 24.  I did not see anywhere where it said you could put 32 in there...

I also added commands to enable GLX (open GL?)

Still nothing

In Linux, 24 bit is 32, I forget the reasoning behind it. But it's all the same.

Edit: Sorry, this was already mentioned above. Im a little slow :)

---

### Post by Shatrat on 2007-02-07
2 things.
First, you might want to install the nvidia binary drivers, I think youll need the **legacy** ones for your card.
There are how-tos all over the place for this.
Second, to make things look sharper on your LCD, there is a configurator in System -> Preferences -> Fonts that really does wonders for making text look sharp.  Just pick whichever preview texts look best.

Theres been a fair ammount of misinformation in this thread, read carefully before you continue.

---

### Post by headlice on 2007-02-07
> **Sunflower1970 said:**
> ...Really? I have two computers using Dell LCD 17" monitors, (one's a Dell Dimension 8200, and the other a Compaq Presario 5630) and both work very well with Ubuntu. Both have nVidia cards, one a 7600GT and the other a GeForce3 Ti 500. I downloaded the nVidia drivers with Automatix, then went into my Xorg.conf file and added in "1280x1024" for the resolution. The newer computer and monitor of the two I have I can use the digital input, the older one is the analog input, but you can't tell which is which. Both give me a crystal clear picture. :)

ETA: muguwmp67 that's what I understand, too 32-bit & 24-bit refer to the same thing

I was just talking to someone who suggested automatix.com.  Ill try that.

---

### Post by headlice on 2007-02-07
> **Shatrat said:**
> 2 things.
First, you might want to install the nvidia binary drivers, I think youll need the **legacy** ones for your card.
There are how-tos all over the place for this.
Second, to make things look sharper on your LCD, there is a configurator in System -> Preferences -> Fonts that really does wonders for making text look sharp.  Just pick whichever preview texts look best.

Theres been a fair ammount of misinformation in this thread, read carefully before you continue.

If automatix.com doesnt help, Ill try to get the drivers from Nvidia's site.  I had the driver yesterday, couldnt figure out how to install it (much less find the darn file in the terminal screen- it was fricken sitting there right on the desktop) and seek instructions on installation.

---

### Post by Shatrat on 2007-02-07
I dont recommend using automatix, it can hose you later on down the road.  
It can mess up the installation of things using the normal apt system.
Use a guide if you want to install the driver.
[http://doc.gwos.org/index.php/Nvidia/Geforce4](http://doc.gwos.org/index.php/Nvidia/Geforce4)

---

### Post by chaplanger on 2007-02-07
Before you think of jettisoning the Dell LCD Monitor -- I am using a 17" Dell monitor (Dell 1704 FPV) and am running it in 1280x1024 resolution at 24 bit color depth -- and it works great.  

That said, I did have to work to get the right Nvidea drivers (I needed the legacy drivers) installed and fiddled with the internal xorg.conf settings a bit 

The Nvidea drivers are found in synaptic package manager.  Install these and your problem may be resolved. . . 

If you search for Nvidea in synaptic it should pull your choices up.

---

### Post by Sunflower1970 on 2007-02-07
> **Shatrat said:**
> Theres been a fair ammount of misinformation in this thread, read carefully before you continue.

What was the misinformation?

I don't understand what is wrong with automatix? It was the only way I could get the drivers to work for me. Envy didn't work, neither did trying to use synaptic.

---

### Post by headlice on 2007-02-07
K, I used Automatix and it d-loaded the new driver for me.

Nothing changed when I did this.  I then went into Applications-> System Tools-> Nvidia Settings (nvidia placed an icon in the menu with the installed drivers)

Then, I clicked on the left menu where it displayed my monitor.

I then changed the Vibrance and watched a pale desktop background change into the vibrant colored environment that I am familiar with......

---

### Post by fenian on 2007-02-07
32 bit color is really 24 bits of color info and 8 bits of alpha channel info or padding space.

---

### Post by irish_flu on 2007-02-07
Contrary to what's been said earlier in this thread, your monitor is NOT the problem.  There are many helpful suggestions here, but changing your monitor to a similar "non-Dell" LCD isn't gonna help.

Dell doesn't even manufacture their own LCDs.

-follow the suggestions for using the best possible driver, whether or not you use Automatix is up to you.

- follow the suggestions about messing around with the effects in Preferences/Fonts


What specifically do you notice looks crappy (sorry if I missed it)?

---

### Post by headlice on 2007-02-07
> **irish_flu said:**
> Contrary to what's been said earlier in this thread, your monitor is NOT the problem.  There are many helpful suggestions here, but changing your monitor to a similar "non-Dell" LCD isn't gonna help.

Dell doesn't even manufacture their own LCDs.

-follow the suggestions for using the best possible driver, whether or not you use Automatix is up to you.

- follow the suggestions about messing around with the effects in Preferences/Fonts


What specifically do you notice looks crappy (sorry if I missed it)?

It was the color display.  Everything looked like it was in 16 bit color display.  There was no sharpness, the colors looked dull and old schoolish.

---

