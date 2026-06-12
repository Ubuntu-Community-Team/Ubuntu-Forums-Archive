---
title: "coming back to 7.04"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by antonio_ing on 2008-01-08
Hi guys

Today I have updated my ubuntu 7.04 to the newest version 7.10.

He asked me, also about the restricted drivers of my graphic board so I installed them also.

When I restarted the pc it was impossible to start with ubuntu and my screen is black. Does someone have some solutions??

---

### Post by browndruid on 2008-01-08
I'm not sure how exactly you would do this, but you may want to add "vga=771" to the boot flags. I needed to do this on the 7.10 live CD to get it to work. I'm just not sure how to do that without a live CD.

Anybody know?

---

### Post by tylerspaska on 2008-01-08
i had that problem. to fix it i had to change my ati driver to the vesa driver. i don't like the vesa driver because it doesn't use my graphics card to its fullest (no beryl or compiz effects and other 3d animations are slow to render), so i ended up going back to 7.04.

anyway, here is now i fixed it. when the screen goes blank or black wait a while for the login screen to load (even though you can't see it it's still working) then go to a console by pressing <ctrl><alt>F1 or maybe F2. then login to the prompt. after login enter 
```
sudo dpkg-reconfigure xserver-xorg
```
go through the setup and select vesa as your graphics driver. there are also some other settings you may want to play with. then hit <ctrl><alt><backspace> to restart x

---

### Post by antonio_ing on 2008-01-08
I think that it's a problem of the new drivers

Does someone know how can I remove the new drivers??

---

### Post by antonio_ing on 2008-01-08
I wasn't able to access linux but now i'm in the recovery mode and i'm in theconfiguring xserver-xorg. How can i reinstall the drivers? should I select the default driver for my ati video card?

---

### Post by antonio_ing on 2008-01-08
It's ok now
thank you for the right suggestion!!!

I entered in the recovery mode  and, by the terminal I have reconfigured the ati video card. Now it is working fine

---

