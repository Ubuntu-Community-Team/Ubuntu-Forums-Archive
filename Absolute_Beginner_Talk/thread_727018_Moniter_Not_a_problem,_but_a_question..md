---
title: "Moniter: Not a problem, but a question."
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by ChromeKaldra on 2008-03-17
Just the other day, [yesterday] i attempted once again to modify my screen resolution to it's max [as i cannot w/o failing so far] Now, my resolution right now is 1024x768, and it fills my entire 19" LCD screen. [Dell 1907FP] But when i try 1280x960, i get a squished [horozontally] high resolution screen with a bar on the right side. And if i try 1152x864 i get only 2/3 of my screen filled [bar on bottom and right, filled w/ ubuntu peachy color] 

So my question is why are these higher resolutions not filling my screen when the lower ones do?

---

### Post by markjensen on 2008-03-17
What video card do you have, and what driver?

If you open a terminal and type in **xrandr** what is listed for the supported resolutions?

---

### Post by pedro_orange on 2008-03-17
When you configure your xserver-xorg it asks you which resolutions your graphics card / monitor can take. Are these enabled?

---

### Post by ChromeKaldra on 2008-03-18
@Markjenson

- ATI Radeon 2600 HD. Driver = Envy installed it for me, so i don't know. Funny thing is, is that i never got my card to work 'properly'. As is, my Graphics card is set to 'generic' but the resolutions i want are still available. [even though envy installed the driver apparently...if i try to choose my card, the screen goes all wacky, with funky colors and no anti-aliasing anywhere.]

- i get this:

```

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  151 (RANDR)
  Minor opcode of failed request:  6 ()
  Serial number of failed request:  9
  Current serial number in output stream:  9

```

@ Pedro

- don't know what you're talking about, so i'm going to have to say...no. :D

---

