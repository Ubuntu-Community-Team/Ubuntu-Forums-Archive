---
title: "Font Quality / Focus"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by awiggin on 2007-05-27
Hey all,

I have been using my Ubuntu 6.06 for a couple months now and I love it...mostly.

I have a problem with my fonts.  They all look out of focus a little bit.  I have tried tweaking the fonts in the System-Preferences-Fonts window, but it hasn't helped.

After a while, it makes it hard for me to look at my Ubuntu desktop and I have to go back to the other guys, which I don't want to do.

Any suggestions?

Peace,
Lance

---

### Post by awiggin on 2007-05-27
Oops - I have Ubuntu 6.10 not 6.06

---

### Post by awiggin on 2007-05-27
Can anyone help me with this?

---

### Post by alienexplorers on 2007-05-27
What video card are you using and are you using the most current drivers.

---

### Post by ramjet_1953 on 2007-05-28
It sounds very much like a video card issue.

With the right driver and resolution setting your fonts should be very crisp.

Like alenexplorers said, post us your video card/chipset info, the native resolution of your screen and we should be able to sort it.

Regards,
Roger :cool:

---

### Post by Michaelt74 on 2007-05-28
Make the fonts in Ubuntu appear similar to the Windows XP fonts (less strain on the eyes)

Install msttcorefonts (System>Administration>Synaptic Package Manager> search for msttcorefonts and install these.

Next, download the xml files and save them to your desktop: xml files

Open a terminal: Applications>Accessories>Terminal

cd Desktop

sudo tar xvjpf fontconfig.tbz -C /etc/fonts/

Remember to reboot for the settings to take effect.

---

