---
title: "Volume control"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by bladefallcon on 2007-01-20
Ok, so I am very confused here. I opened the volume control, and see 3 sliders. Master, PCM and PC Speaker. PC speaker is muted..ok whatever. Master doesnt do ANYTHING. I mute it, i still get sound. I turn it down, volume is unaffected. PCM is the only one that effects my volume level. What is going on? I have a macro button on my keyboard that can control the volume, but it only controls the master volume...which doesnt do anything...

---

### Post by ahaurw01 on 2007-01-21
I had the same problems when installing to my laptop. I thought that I was not getting sound at all from Ubuntu, then realized I had to use the headphone jack and only the headphone slider would change the volume. When in the volume controls you can select edit > preferences to choose which controls are necessary for you. Hopefully you'll have some luck changing the level on that channel. Also, if you find that works for you, what I did is right click the volume icon in the notification area and select it to change just the headphone channel when it is clicked only once under 'preferences.'

Aaron

---

### Post by bladefallcon on 2007-01-21
Ok..that did half the job. Now, adjusting the valume from the icon in the system tray does do what i need it to do, but still, the macro button which controls the volume is still doing the same. It is still only changing the master volume, which does nothing.

---

### Post by ahaurw01 on 2007-01-25
Yeah, I have the same issue here. I wouldn't use it that much anyways, so I kind of forgot about it. It's probably something in the underlying keyboard configuration that would be near impossible for me to figure out how to change. Sorry for the late post. Let us know if you figure it out, I'm curious now, too.

Aaron

---

### Post by ComplexNumber on 2007-01-25
> **bladefallcon said:**
> Ok, so I am very confused here. I opened the volume control, and see 3 sliders. Master, PCM and PC Speaker. PC speaker is muted..ok whatever. Master doesnt do ANYTHING. I mute it, i still get sound. I turn it down, volume is unaffected. PCM is the only one that effects my volume level. What is going on? I have a macro button on my keyboard that can control the volume, but it only controls the master volume...which doesnt do anything...
the reason why is because you haven't selected the sound card which is being used to make the sound. go to 'file' and then 'change device'.

---

### Post by bladefallcon on 2007-01-25
> **ComplexNumber said:**
> the reason why is because you haven't selected the sound card which is being used to make the sound. go to 'file' and then 'change device'.

changing that does nothing at all. It lists 3 devices: 

SAA7134 (Alsa Mixer)
Via 8237 (Also mixer)
SAA7134 Mixer (OSS Mixer)

The second one is the one selected (as it is the only one that allows me to do anything with the PCM volume) 

I have tried switching to the others, but it has no effect.

---

### Post by mlissner on 2007-02-09
I read a minute ago this is fixed in Fiesty for Asus laptops. I haven't tried it yet though...

---

