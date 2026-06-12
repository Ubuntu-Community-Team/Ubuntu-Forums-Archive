---
title: "Mouse freezing when Rythmbox is playing"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Katana000 on 2007-10-26
I have looked for this subject, but I haven't noticed anything close enough to help.

I often listen to music through Rythmbox as I work on my PC. After a clean install of Ubuntu 7.10 64 bit, I have noticed that the mouse will freeze while the music continues. I can still use the keyboard to tab through the screens, but the mouse does not move. I have a ECS K8M890M-M, 4400 dual processor AMD 64. I use the onboard video and sound and I have 2 gig of ram.The mouse is a generic PS/2 type.

If anyone has suggestions on where to look or how to overcome this, please let me know. Every time I sit down to compute, I forget about this until the mouse freezes and I have to reboot and start over.

Thanks

---

### Post by agurk on 2007-10-26
Just to help you narrow things down a bit:

* Try playing music using VLC or Audacious instead (both available in Synaptic) - does the same problem occur?
* Does disabling Compiz Fusion make any difference? (System --> Preferences --> Appearance --> Visual effects: None)

---

### Post by Katana000 on 2007-10-26
I was able to play music without mouse problems using VLC. Does this indicate something that can be corrected so I can keep using Rythmbox?

---

### Post by Crafty Kisses on 2007-10-26
Try seeing if anything is using up a lot of resources, you can do that by opening up the terminal and doing the following: ```
top
```

---

### Post by Katana000 on 2007-10-26
Codename,
I opened up terminal as you suggested and entered 'top', and got a long list of applications, but I'm not sure what I should be looking for. Rythmbox shows to be opened, but as soon as I tried to open my picture file the mouse froze. This file is very large (13,000 photos), could that be a problem? I can attach the screen print if needed.

---

### Post by agurk on 2007-10-27
Any luck with Compiz Fusion disabled?

---

