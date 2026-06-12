---
title: "TV Display crappy! xubuntu"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2006-10-06
Ok so i've just getup my linux box with xubuntu. Yay all good.

Then I unpluged it from the monitor to put in the living area. Watch DVD's etc.

Pluged in the TV booted up and oh NO!!! it looks like crap! I can't see anything. It's like blured/fuzed on the screen!

Something tells me I should have installed it with TV pluged in.

I can still use it though VNC so I can change things easly. I tryed lowering the resolution but ono such luck.

Anyone got any ideas?

---

### Post by fragos on 2006-10-06
To view TV you need a TV tuner card like the WinTV-GO.  Hook your antenna to the card and use an application like tvtime.  Works great for me.  If you want to use your TV for a minitor you need a video card with an S-video TVout or a DVI interface on bothe video card and the TV.

---

### Post by guysmiley25 on 2006-10-06
The video card I have has a what I think is called an RCA? Like the playsation cables.

But thanks for the help i'm looking to to upgrading my video card anyways. Do you or anyone have an recommendations? I want to plug into a wide screen TV that supports RCA and S-Video.

---

### Post by fragos on 2006-10-06
A lot of Nvidia cards have an S-video TVout including my FX5200.  I'm happy with Nvidia although I haven't used the TVout.  I watch TV on my PC screen in a window or full screen.

---

### Post by MetalMusicAddict on 2006-10-06
> **guysmiley25 said:**
> The video card I have has a what I think is called an RCA? Like the playsation cables.

But thanks for the help i'm looking to to upgrading my video card anyways. Do you or anyone have an recommendations? I want to plug into a wide screen TV that supports RCA and S-Video.
If you are actually going for a Hidef widescreen, plasma or LCD, use the DVI output with a HDMI converter. It looks like those dongles that you use on a DVI to go to RGB. This will gige you the best picture. COmposite and s-video just dont give a good enough picture.

I have a ubuntu box hooked up to a 43" plasma. I have a DVI input on the back of my set though.

---

### Post by Titus A Duxass on 2006-10-07
I run mine through S-Video and have a good picture when screening movies, etc.  However, the desktop and the browser are not so good, readable but you can see the pixellation of the TV.

Are you setting your resolutions in the xorg.conf file?

---

### Post by guysmiley25 on 2006-10-09
I have just been playing around with the xorg.conf file. Every attempt leads to X not starting!!!

I was just wondering if it could be the resolution and then refresh rate? Because it is displaying its just all over the place.

---

### Post by guysmiley25 on 2006-10-09
I have managed to get it working using aticonfig. But It still is not great. It is not positioned on the screen correctly. Could be due to widescreen + big resolution cause It changed after running aticonfig --initial. But at least I can see somthing. Look's like i'm going to have to get a new video card cause I want somthing better anyways. But for the mean time has anyone got any ideas on how I can configure this? also what card would people recommend? I want to setup mythTV in the end.

---

### Post by guysmiley25 on 2007-01-01
After a reinstall there is no problem. So I guess this is not an issue anymore.

---

### Post by whoscheesemine on 2008-03-22
I'm using Xubuntu, how do you switch between the monitor and tv? On my laptop I just hit the Fn + f4 keys. I'm aware that I don't have that shortcut on my desktop keyboard, but if someone knows the terminal command for it I could map a key for it. Does anyone possibly know how to do it using the GUI? and YES! I've checked screens and graphics!

_**[COLOR="Red"]EDIT:[/COLOR]**_

Well, come to find out, in "NVIDIA X Server Settings", all I had to do was go into the "X Server Display Configuration" and change the TV Resolution to "Auto" and the Position to "clones", keeping the monitor with Resolution at "1024 x 768" and Position at "Absolute". I hit apply and, that works perfectly fine for the same display on my monitor as on my TV. 

However, whenever I try to put something into fullscreen (from a media player that is, myspace works fine as its not actually truelly fullscreening) my tv cuts off and only the monitor continues to work.

Whenever I go back into my "NVIDIA X Server Settings" I see that all my settings are set back to what they were before the TV cutoff. Once again, I can set everything to what I said I had things at previously and once I hit apply, BLAM! It's back to being on both screens... but if I put anything back into fullscreen then its back to having only my monitor again. 

What can I do to make it so that once, I put something into fullscreen it will remain on my TV as well?

---

