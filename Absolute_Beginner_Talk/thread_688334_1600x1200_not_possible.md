---
title: "1600x1200 not possible?"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by JapanFred on 2008-02-05
Hi guys,

This is my first time using ubuntu, everyone i know has been raving about it so i thought i should give it a try. I have used Fedora and Gentoo in the past, with no issues at all.

But i've been using ubuntu for 10minutes, and i can't get my display drivers showing the correct reso? I've got an old iiyama 19" that displays 1600x1200 over DVI, and a Bravia (DVI-HDMI) that displays 1920x1080p on windows fine. never tried the Bravia in Linux before as i didn't need to, and i don't really need to now, it's just a nice toy.

But i really need my reso for the main monitor @ 1600x1200, i think it's only showing at 1024x768 at the moment, and looks terrible as you can imagine. I've got the NVIDIA drivers installed (running on a 8800GTS) and i get the pretty NVIDIA Logo on bootup.

But if i set my monitor to Generic 1600x1200 LCD Display, select the reso of 1600x1200, restart X, the visible area is still only 1024x768! It just pans around when i hit the edge of the screen, which is just horrible.

I've attached the XOrg Config file, should it be of any use.

I am running uBuntu 7.10 Gutsy Gibbon.

uname -a
```

Linux dean-desktop 2.6.22-14-generic #1 SMP Thu Jan 31 23:33:13 UTC 2008 x86_64 GNU/Linux

```

Looking forward to a response!!

Cheers guys,

Dean

---

### Post by Nythain on 2008-02-05
edit: nevermind if you saw previous... i was retarded... and at this point, i dont know

edit again: what happens if you try to change your resolution using
```

gksu nvidia-settings

```
and save the changes and reboot???

---

### Post by JapanFred on 2008-02-05
I can't even select 1600x1200 in that panel...it's really weird the max reso there is is 1024x768 :(

---

### Post by Nythain on 2008-02-05
hmmm... what method did you use to install your nvidia drivers???
Envy
Nvidia's website instructions
or nvidia-glx-new package???

---

### Post by rkd on 2008-02-05
I don't know whether it matters, but did you install the nvidia drivers from the Restricted Drivers Manager, or did you get them from somewhere else?

---

### Post by JapanFred on 2008-02-05
I used the restricted drivers manager bit...as the ubuntu guide told me to do.

---

### Post by Nythain on 2008-02-05
so, at this point, im not sure if it will help but you could try
```

sudo dpkg-reconfigure xserver-xorg

```
and set up a fresh new xorg.conf that way, see if it will get ya any closer

---

