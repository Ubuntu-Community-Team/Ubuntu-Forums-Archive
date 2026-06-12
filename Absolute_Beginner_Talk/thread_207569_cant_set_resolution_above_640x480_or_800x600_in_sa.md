---
title: "cant set resolution above 640x480 or 800x600 in safe mode installer"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by 3037 on 2006-07-02
hi, ive got a problem installing ubuntu on an older pc.  its a 733mhz pentium and i cant set the resolution higher than 640x480 or 800x600 in safe mode installer.  i think the problem could be the video card which is a very old trident pci card.  in windows i can set the resolution to a max of 1024x768(i think, mite b higher)

---

### Post by someusernoob on 2006-07-02
I think you have to add the 1024 resolution manually to your xorg.conf file but as far as i know that doesnt work while you using the live cd.

I dont know what your plans are with the live cd, but if youre gonna install Ubuntu and the resolution isnt still "supported" do this:

Open a terminal (applications >acces. > terminal) and type (or copy-paste so you dont have typo's):
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

--(here it asks for your password)--

sudo gedit /etc/X11/xorg.conf

```

And then you'll see have way down the file some resolutions and there you have to add "1024x768" in each line.

---

### Post by 3037 on 2006-07-02
sorry i mustnt have been clear about what i woz doing.  i meant to say that i had installed ubuntu, but resolution was 640x480max so i reinstalled using safe mode installer and then i got max 800x600.  ill try ur sugestion now.

---

### Post by 3037 on 2006-07-02
ok found the problem.  everything in xorg.conf was rite xcept the crappy old monitor i woz using cudnt do 1024x768@24 colour depth.  so i lowered colour depth to 16 and it worked although it looks kinda crappy.  thx for the help

---

