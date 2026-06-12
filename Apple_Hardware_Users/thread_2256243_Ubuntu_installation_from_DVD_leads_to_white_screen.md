---
title: "Ubuntu installation from DVD leads to white screen"
date: 2014-12-10
forum: Apple Hardware Users
---

### Post by ben_westcott on 2014-12-10
HelloI am installing lubuntu onto my PowerBook g4 ppc Mac and when I booted off of my installation disk for Ubuntu, it asked me to boot which I did and then it started booting then the screen turned black and then it started fading in white with little strips of colored lines going down the screen. Does anyone know how to fix this will I have to get a newer version of the operating system 
Thankyou in advance

---

### Post by este.el.paz on 2014-12-12
@Ben:

I'm assuming you mean "iMac"???  You aren't mentioning which version you are trying to install . . . it can be a little technical installing to an iMac . . . search the forum for threads relating to "12.04 on iMac G4/G5" & the recently posted to "nv driver on iMac 800" (something like that, posted on here in the last week or so) . . . you will probably need to add an xorg.conf file for your model, and you will need to adjust that xorg.conf file to fit your video driver . . . .  Before you could find instructions on "retro-installing 'nv'" . . . but now you will probably use "fbdev" . . . and set the "refresh rates" for the screen . . . .  It will take some time to learn the various things you need to do . . . try out the "PowerPCFAQ" wiki and read through that as well.  Some of these steps will need to be done in the TTY . . . likely w/o benefit of screen . . . it can be highly "amusing."

e.e.p.

---

