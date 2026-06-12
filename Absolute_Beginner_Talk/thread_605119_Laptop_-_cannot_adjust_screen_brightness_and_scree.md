---
title: "Laptop - cannot adjust screen brightness and screen remains black after suspend"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Jonathin on 2007-11-06
I am using Ubuntu 7.10 on my brand new T61p ThinkPad.

When I use function keys on my keyboard, Ubuntu displays a little box with a light in it (looks like a sun) and despite the bar moving, the screen will not get darker or lighter. I have also tried to go to power management, but adjusting the brightness there does absolutely nothing.

Also, when I close the lid of my laptop, it puts my laptop on suspend, which is good. However, when I open the lid, the screen turns and white text goes across really fast, and then the monitor shuts off and I cannot get it to come back. I have tried the ctrl+alt+f1 then ctrl+alt+f7 trick, but that does nothing.

Any help would be great! Thanks!

---

### Post by bluepowder7 on 2007-11-06
i've had a similar experience with the brightness issue on my gateway, where it is either OFF or ON, and with steps from 0 to 20, it only turns the screen ON at steps 5, 10, 15, and 20.  irritating to say the least...

so, basically, i have no solution, and only sympathy to offer.  i just keep my screen set at full brightness until a solution is released...

i haven't tried the suspend thing though.  i just have it set to turn off the screen, and fully shut down if battery power is too low.  i've avoided suspend and hibernate since the days of Win2k.

---

### Post by systemintheglitch on 2007-11-07
I have a similar problem.
I am wondering if you guys, upgraded from an earlier ubuntu. 
I'm thinking that could be the problem.

---

### Post by P4man on 2007-11-07
Not sure this will be much help, but I had the exact same problems on my Acer using Gutsy Tribe 3/4/5.  It was solved for me either with the release version, or if not, then  through an update shortly after. 

Did you install all updates ?

---

### Post by bluepowder7 on 2007-11-07
mine is a fresh full install (not an upgrade), and i tend to install all updates as they become available, rarely more than 2 days go by before i do that.  i was wondering if there's some funky way of grabbing the display manager thingy from 7.04 and using that in place of the 7.10 display manager.  in my case, the brightness control worked swimmingly in 7.04

---

### Post by Jonathin on 2007-11-09
I noticed after I open my laptop lid after suspend, and the text flashes across the screen before the screen goes blank, that my caps lock light is flashing, which I assume means there is a kernel panic.

does anyone know what log file I would look under in /var/log?

Are there any thinkpad drivers that I need to install? (is there a simple apt-get command?)

---

### Post by Jonathin on 2007-11-14
I fixed the suspend issue, but I am still having problems adjusting screen brightness.

Follow these steps to fix suspend:
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T60#Suspend_to_RAM](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T60#Suspend_to_RAM)

---

### Post by scoobu4844 on 2008-03-01
i am reviving this thread becuse i have the sme problem.  none of my function keys work.  is their an aplication i can download that willallow me to adjust my screen brightness in it?it is gusty

---

