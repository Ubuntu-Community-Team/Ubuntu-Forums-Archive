---
title: "Bongo Drum Noise"
date: 2005-07-09
forum: Absolute Beginner Talk
---

### Post by g0sp3L on 2005-07-09
I just installed ubuntu on my mom's machine and for some reason I get a constant bongo drum sound coming through the speakers. Could it be some sort of alert? (never used ubuntu before) Email me to let me know please! :) Thanks

---

### Post by aysiu on 2005-07-09
[QUOTE=g0sp3L]I just installed ubuntu on my mom's machine and for some reason I get a constant bongo drum sound coming through the speakers. Could it be some sort of alert? (never used ubuntu before) Email me to let me know please! :) Thanks[/QUOTE] Go to System > Preferences > Sound and uncheck the box that says  "Sound for events."

The annoying drum sound happens when you click stuff. I hate that sound.

---

### Post by TravisNewman on 2005-07-09
Some computers I've seen (wife's computer is really bad about this) will get stuck on sounds, so it keeps playing a certain sound OVER AND OVER again. Is it constant, or is it when you clock on something?

---

### Post by aysiu on 2005-07-09
Should be when you click on something or if there's a warning. I'd just turn off the sound for events in general.

---

### Post by sapo on 2005-07-09
[QUOTE=panickedthumb]Some computers I've seen (wife's computer is really bad about this) will get stuck on sounds, so it keeps playing a certain sound OVER AND OVER again. Is it constant, or is it when you clock on something?[/QUOTE]

lol.. i just imagined that kind of sounds.. OMG there is a tribe inside my bedroom.. they are gonna eat me  :roll:

---

### Post by g0sp3L on 2005-07-11
Ok, I turned off sound for events entirely, but it's still there. It's a constant drum noise, no pause or silence in between. Don't know what could be causing this. Is it possible to just delete the .wav file or would that cause more problems (i.e. error messages, etc.)?

---

### Post by Hunnamus on 2005-07-14
I got that sound off but I don't remember how, I must get home first. I'll tell it on sunday. It was drumming all the time and it made me mad :D

---

### Post by Error_Msg on 2005-07-14
[QUOTE=g0sp3L]I just installed ubuntu on my mom's machine and for some reason I get a constant bongo drum sound coming through the speakers. Could it be some sort of alert? (never used ubuntu before) Email me to let me know please! :) Thanks[/QUOTE]

I had that happen when doing an /etc/init.d/gdm restart after fiddling around with my video card seetings in xorg. The bongo sound from the splash screen got stuck playing over and over. I was quite folkloric though.
It would go back to normal after rebooting. In your case, I'm not sure what the problem is, but I would start with changing the sound settings to ALSA.

E_M

---

### Post by atilasendil on 2005-07-16
[QUOTE=sapo]lol.. i just imagined that kind of sounds.. OMG there is a tribe inside my bedroom.. they are gonna eat me  :roll:[/QUOTE]
 Which reminds me of :

This guy goes on vacation to a tropical island. As soon as he gets off the plane, he hears drums. He thinks "Wow, this is cool." He goes to the beach, he hears the drums, he eats lunch, he hears drums, he goes to a luau, he hears drums. He TRIES to go to sleep, he hears drums. This goes on for several nights, and gets to the point where the guy can't sleep at night because of the drums. Finally, he goes down to the front desk. When he gets there, he asks the manager, "Hey! What's with these drums. Don't they ever stop? I can't get any sleep."

The manager says, "No! Drums must NEVER stop. Very bad if drums stop."

"Why?"

"When drums stop...bass solo begins."

---

### Post by jeriziosantos on 2005-10-10
[QUOTE=g0sp3L]Ok, I turned off sound for events entirely, but it's still there. It's a constant drum noise, no pause or silence in between. Don't know what could be causing this. Is it possible to just delete the .wav file or would that cause more problems (i.e. error messages, etc.)?[/QUOTE]

i have the same problem, i have no idea how to get rid of the noise, (1st time user) can someone tell me how to get rid of it? 

email me at [email]jeriziosantos@hotmail.com[/email]
i will be so pleased if someone can actually help me get rid of it

---

### Post by mokeyjoe on 2005-10-10
I had that problem. I have a sound blaster card installed so I turned off the on-board integrated sound in the BIOS and it cured this.

Sound works perfectly now (but I still turned off the damn bongo noise ;) )

---

### Post by Efwis on 2005-10-10
I had that problem myself when I first installed Ubuntu. turns out it has something to do with the AC'97 chipset for the onboard soundcards that some MOBO's use. 
After mine died I put in a new MOBO with the Realtek chipset no problems from then on.

click on **system>Administration>Login screen setup** then click on the **Accesibility **tab.
Once there uncheck the box that says **make a sound when login window is ready** 

That will solve your problem.

---

### Post by jeriziosantos on 2005-10-12
that does work, however, now whenever i go to load ubuntu nothing happens after password input. any ideas?

---

### Post by Efwis on 2005-10-12
[QUOTE=jeriziosantos]that does work, however, now whenever i go to load ubuntu nothing happens after password input. any ideas?[/QUOTE]
did you make sure the System sounds were disabled also under **Preferences>sound> remove the check box from "enable sound server startup"**

unfortunately the only problem with this is you have no sounds other then when you are on the internet or playing a CD/DVD

If you dont' have it unchecked it will freeze your system up.

---

### Post by jeriziosantos on 2005-10-12
i didnt the second time, the first time i did thought i had no sound on at all and it still made my system freeze (i reinstalled it and tried again) maybe i have a dodge copy of unbuntu or something

---

