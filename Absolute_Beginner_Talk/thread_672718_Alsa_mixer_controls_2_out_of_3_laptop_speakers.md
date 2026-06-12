---
title: "Alsa mixer controls 2 out of 3 laptop speakers"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by rockstar on 2008-01-19
I have a Dell XPS Gen 2 laptop.  My laptop does not control the subwoofer on the bottom of the laptop.  When the master volume is muted, the bottom speaker does not mute.  I'm not sure what's wrong but here's some troubleshooting.

When the Master Volume is muted and the PCM is Muted then the speaker turns off.

When the Master Volume slider and the PCM slider is moved at similar levels, then the three speakers sort-of balance out.

When Headphones are plugged (speakers bipassed) no problems.

Somehow all three speakers are working, but the subwoofer cannot be controlled.  Are there drivers I'm missing?  I've read about bipassing things with this link in a similar thread, but it had to deal with surround sound:

[http://alsa.opensrc.org/How_to_use_softvol_to_control_the_master_volume](http://alsa.opensrc.org/How_to_use_softvol_to_control_the_master_volume)

---

### Post by charlesbrooking on 2008-02-14
> **rockstar said:**
> I have a Dell XPS Gen 2 laptop.  My laptop does not control the subwoofer on the bottom of the laptop.  When the master volume is muted, the bottom speaker does not mute.

On my Dell laptop, the subwoofer volume control is labelled 'Master Mono'. You might need to enable that track using 'Edit > Preferences' in the Volume Control.

If that works, you might also find this helpful: open 'System > Preferences > Sound' and, in the 'Default Mixer Tracks' section, select both Master and Master Mono. This means that when you hit the multimedia buttons on your keyboard to increase or decrease volume, it will move both the main speakers and the subwoofer at the same time.

---

### Post by rockstar on 2008-03-24
I haven't been on the forums for a while, but this seemed to help me find the master and master mono on Alsa but the selecting both didn't seem to work.

Also for some reason there is a second device listed called: SigmaTel STA9750,51 (OSS mixer) that doesn't seem to do anything

Thanks

---

