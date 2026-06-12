---
title: "Widescreen support"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by tygr88 on 2007-10-05
Ok i am really really new to linux so bear with me.I lave linux 7.04 and the gui i use does not suppot a resolution of 1440 by 900 pixels. the maximum it supports is 1024 by 768.Is there any gui which supports a widescreen resolution??

---

### Post by elliotjreed on 2007-10-05
I had the same problem. I downloaded Xorg-edit, and added 1440x900 in the screen section.

That didn't work when I installed on another computer, so I did:

```
sudo dpkg-reconfigure xserver-xorg
```

Then selected my video card, the screen resolution!

Try the second one first, as it is a safer option. But I would save a backup of your xorg.conf, so that if it all goes wrong you can run the live CD and put it right! Worked for me tho!

---

### Post by rustybronco on 2007-10-05
Not that I able to help much, I'm a "noob" as it were, I will do what I can to help.
 what video card or video chip set are you using?

---

### Post by LowSky on 2007-10-05
```
sudo dpkg-reconfigure xserver-xorg
```

this will reconfigure your hardware settings be careful when doing this.
If your not sure about configuring your  hardware by hand please be careful, and carefully read everything before changing settings.
Be careful in picking your video drivers as they can mess the start up of gnome

---

### Post by rustybronco on 2007-10-05
Most of time yes, but one time i had to " sudo gtf 1280 800 60 " in the terminal and then paste the output of that into /ect/X11/xorg.conf and save it.
to get my old ati 7000ve card to work @ 1440x900 60hz

---

### Post by bsharp on 2007-10-05
something else you could do (especially if you have a nVidia card) would be to install the closed-source drivers and use the tool that comes with them to set the resolution.

---

### Post by tygr88 on 2007-10-06
i have a geforce 8600

---

### Post by mrmonday on 2007-10-06
As lots of people have said, go to Applications > Accessories > Terminal, and paste:

```
sudo dpkg-reconfigure xserver-xorg
```

Hit enter, then enter your password and follow the instructions. If prompted for a driver choose nv or nvidia. You might also want to enable nvidias restricted drivers using the restricted drivers manager ( System > Administration > Restricted drivers manager).

---

### Post by ashfaq.s on 2007-10-06
> **rustybronco said:**
> Most of time yes, but one time i had to " sudo gtf 1280 800 60 " in the terminal and then paste the output of that into /ect/X11/xorg.conf and save it.
to get my old ati 7000ve card to work @ 1440x900 60hz

Dear, I am a total newbee to linux world, facing problem with resolution in viewsonic VG1930wm. I need the resolution of 1440x900, will uou please help me out with clear and simple how to?

I did not understand the copying of the outcome and than navigating and doing the pasting. Please!
Ashfaq

---

### Post by tygr88 on 2007-10-06
thanks a lot and ashfaq follow the method in the post above urs

---

