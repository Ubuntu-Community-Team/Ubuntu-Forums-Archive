---
title: "No Screen error"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by bunnybash on 2007-07-27
I am trying to install Ubuntu 7.04 on my Asus A6J...

Intel Core Duo
ATI X1600
1Gb

Anyways i cannot even boot the live CD as it comes up with an error half way through saying that it cannot find a screen, which is really annoying because it is telling me this on a screen!!!

GDM error or something... man it is confusing...

I tried booting Gparted too, and it cannot find me a screen either... even after choosing the drivers and resolution...

Any suggestions??

I really want to install Ubuntu Studio, but wanted to run the live CD first to make sure that everything worked...

---

### Post by ddrichardson on 2007-07-27
It means it cannot find a configured X screen, so there is a problem with the X config. There may be a workaround - what is the error message that GDM shows?

---

### Post by mrshaftino on 2007-07-27
You could reconfigure the X server from a virtual terminal, or just use the alternative install....your choice?

---

### Post by andrewwesley on 2007-07-28
Greetings from Germany

I'm totally new to Ubuntu. 

I've just installed ubuntu studio 7.04 from the alternative ISO image
it seems like I have a similar problem
everything works "fine" - the machine boots up, the splash screen is displayed - but then the screen switches off, comes back on and is totally "dark" 
Even so, I can enter my log in (blind) - and the log on audio file is played. So I assume all else is OK at the moment. 
I pressed a few ctrl+alt+F keys - and was returned to a console
In the console I read a few lines - something like 

  splash at 1024x768 failed
  spalsh at 800x600

During the install I was sure activate all screen resolutions up to but not including the 1400x  ones.

The hardware is an old compaq deskpro with P3 866MHz and 256MB  SDRAM
using the onboard graphic device (no AGP grahic card yet) 
monitor is a Hyundai B71A flat screen - which supports a very wide range of settings. 

Strange - because Ubunutu 7.04 was working well - just a few blue streaks down the screen at certain screen resolutions - but I found one which was working fine. 

how do I configure screen settings ? Do I have to do a complete reinstall ? 

yours hopefully 

Andy

---

### Post by bunnybash on 2007-07-29
> **ddrichardson said:**
> It means it cannot find a configured X screen, so there is a problem with the X config. There may be a workaround - what is the error message that GDM shows?

It just tells me that there is a problem with X server and the screen goes all crazy on me and it asks me if i want to debug it, but i have no idea how to do that or what it means...

i am really really newb...

not sure what alternate install means but i would try that if i knew!! 

REALLY newb!

---

### Post by ddrichardson on 2007-07-29
The alternative cd installs from text mode but wont configure a problem display, but you can install it with this then manually configure your screen. Look up xorg.conf and fill it out with the correct settings.

---

### Post by bunnybash on 2007-07-29
> **ddrichardson said:**
> The alternative cd installs from text mode but wont configure a problem display, but you can install it with this then manually configure your screen. Look up xorg.conf and fill it out with the correct settings.

where do i look up xorg.conf? what do you mean by that... i am sorry for my ignorance!!!  setting up linux is waaaaay different to windows, a whole new language that i am trying to learn, but yeah i cannot imagine how annoyed you must be with such ignorant, inane questions!

---

### Post by ddrichardson on 2007-07-29
Not at all, I should have been more specific. Your display driver in Windows is installed as part of the OS, in Linux it is a combination of a server for your graphics card and a configuration file telling that server how to operate the hardware.

/etc/X11/xorg.conf is where this configuration is stored and if you use:
```
sudo dpkg-reconfigure xserver-xorg
```

Answer the questions and you should get somewhere.

---

### Post by bunnybash on 2007-07-30
> **ddrichardson said:**
> Not at all, I should have been more specific. Your display driver in Windows is installed as part of the OS, in Linux it is a combination of a server for your graphics card and a configuration file telling that server how to operate the hardware.

/etc/X11/xorg.conf is where this configuration is stored and if you use:
```
sudo dpkg-reconfigure xserver-xorg
```

Answer the questions and you should get somewhere.

thanks so much... i think i will be able to do something with that!!  wow... hope!!! :D

---

