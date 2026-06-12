---
title: "Playing with Beryl and screwed up"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by ferpadro on 2007-06-07
A few minutes ago i decided to enable desktop effects, and now everytime i login into ubuntu my screens goes completely white. If i press alt + tab i can see a bit of the multitasking icons, the transparecy and such but nothing more. I didnt remember that my graphic card didnt have direct rendering enabled, so i cant do anything right now except entering the terminal. How can i solve this?

Thanks in advance

---

### Post by Fitzy_oz on 2007-06-07
> **ferpadro said:**
> A few minutes ago i decided to enable desktop effects, and now everytime i login into ubuntu my screens goes completely white. If i press alt + tab i can see a bit of the multitasking icons, the transparecy and such but nothing more. I didnt remember that my graphic card didnt have direct rendering enabled, so i cant do anything right now except entering the terminal. How can i solve this?

Thanks in advance

From the terminal you can remove beryl by typing sudo apt-get remove beryl or beryl-manager.  That should get rid of it for you, you will just need to re-install it after that.

Curiously, what card are you using (ATI, Nvidia, Intel?)

---

### Post by ferpadro on 2007-06-08
lmao im using a SIS 670 with 64 MB. Ill try uninstalling bery, thanks for that

---

### Post by ferpadro on 2007-06-08
I entered a terminal and typed "sudo apt-get remove beryl" and "sudo apt-get remove beryl-manager" but the OS told me i do not have them installed. Well in fact that is true, i never installed beryl, i only enabled desktop effects in system -> preferences. I assumed it was beryl. If its not beryl, how can i change this. I could try to disable desktop effects the same way i did to enable them, but i cannot see anything, just white. Maybe some terminal command would help me, what do you say guys?

Cheers

---

### Post by starcraft.man on 2007-06-08
> **ferpadro said:**
> I entered a terminal and typed "sudo apt-get remove beryl" and "sudo apt-get remove beryl-manager" but the OS told me i do not have them installed. Well in fact that is true, i never installed beryl, i only enabled desktop effects in system -> preferences. I assumed it was beryl. If its not beryl, how can i change this. I could try to disable desktop effects the same way i did to enable them, but i cannot see anything, just white. Maybe some terminal command would help me, what do you say guys?

Cheers

Ok, first off desktop effects is Compiz. Now they are merged projects, before they were separate. I'm not sure about this but you can try it... I am a Beryl user after all and never gotten white screened.

```
sudo aptitude remove --purge desktop-effects compiz compiz-core compiz-gnome compiz-gtk compiz-plugins
```

That should get it all out. In future ya should be a bit more careful. Then do:

```
sudo reboot
```

and you should have your screen back.

If that doesn't work, I'm not sure... it should though, I think so. If someone else has an easier way feel free to correct.

---

### Post by arvinoids on 2007-12-09
Did this resolution work? I have a similar problem, but my screen turns white only after logging on to my own desktop from GDM. I had it resolved by logging in using failsafe GNOME and then disabling desktop effects from there.

---

