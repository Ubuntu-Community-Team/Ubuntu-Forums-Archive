---
title: "Need Drivers"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by CoCoKnots on 2008-04-10
Last week-end I took the plunge & formated my Sony notebook with a fresh load of Ubuntu Linux. I found out after doing so, drivers do not transfer or translate as easy as expected. I am working on a Sony VAIO VGN-FE780G . I need drivers for my Fujitsu DVD player.. My Inlel 3945ABG... ipw needs translated to iwlwifi for my wireless and some kind of driver for my motion eye camera, which I have't even started to get to yet.. I can't open the files I have downloaded to do this change over... Not even the Java download. It appears that I'm required to be a programer to make this transition. Don't get me wrong... I'm very happy with the look & speed of Ubuntu. Are there any drivers out there that will work without modify them in some way... without delete lines & add others. I'm new to this stuff & I don't even know where to begin. It can't (or shouldn't) be that hard. Please Help :(

---

### Post by wolfen69 on 2008-04-10
what about your dvd player that doesnt work? go to system>admin>restricted drivers manager for your intel wireless. dont know about the webcam.

but first go to system>admin>software sources and make sure all boxes are checked. close and reload.

---

### Post by CoCoKnots on 2008-04-10
Thanks for the reply Wolfen 69... The Intel Pro/wireless 3945 for linux is checked enabled.
I tried checking all the boxes in software sources as you suggested. It doesn't make any difference... Im I missing something realy simple here ???

---

### Post by stchman on 2008-04-10
> **CoCoKnots said:**
> Last week-end I took the plunge & formated my Sony notebook with a fresh load of Ubuntu Linux. I found out after doing so, drivers do not transfer or translate as easy as expected. I am working on a Sony VAIO VGN-FE780G . I need drivers for my Fujitsu DVD player.. My Inlel 3945ABG... ipw needs translated to iwlwifi for my wireless and some kind of driver for my motion eye camera, which I have't even started to get to yet.. I can't open the files I have downloaded to do this change over... Not even the Java download. It appears that I'm required to be a programer to make this transition. Don't get me wrong... I'm very happy with the look & speed of Ubuntu. Are there any drivers out there that will work without modify them in some way... without delete lines & add others. I'm new to this stuff & I don't even know where to begin. It can't (or shouldn't) be that hard. Please Help :(

Did you install Ubuntu with your DVD drive?

The 3945ABG is supported with the restricted drivers, they should be enabled by default.

Refer to my website to get your PC playing Hollywood DVDs and other proprietary CODECs working.

---

### Post by aeiah on 2008-04-10
wolfen told you to check the sources boxes because you may need things from these extra repositories some time in the future, as you sift through what's wrong and how to fix it. so dont expect checking those boxes to do anything in and of themselves, they just need to be checked as a starting point.

so, in the intel wireless is checked as enabled eh? so does this work as it should?

and dont worry, you arent required to be some kind of programmer. some programs and drivers require you use the command line, but it isnt as hard as it looks.

you say your dvd player needs drivers. what is the problem with your dvd drive? is it just that you cant play dvd movies? this is to be expected. ubuntu doesnt let you do it by default because it is illegal to distribute the code for that functionality without paying someone royalties. ubuntu lets you make that choice on your own :)

to get dvds and other multimedia to work, copy and paste this line into a terminal and hit enter (in your menu go to accessories > terminal)
```

sudo apt-get install ubuntu-restricted-extras

```

---

### Post by CoCoKnots on 2008-04-10
Thanks Stchman, The Intel 3945 ABG driver is checked enabled... However, it is not working. I'm headed for your web site now... Thanks, Cal

---

### Post by oldos2er on 2008-04-10
Just to add to what aeiah told you, you'll need to install libdvdcss2 from the Medibuntu repository if you want to play commercial DVDs. See [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by wolfen69 on 2008-04-10
you need to go to system>admin>network to get your wireless settings done.

---

