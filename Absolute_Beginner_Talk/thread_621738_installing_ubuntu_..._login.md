---
title: "installing ubuntu ... login?"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by sober2007 on 2007-11-24
i recieved ubuntu in the mail today. i tried to install it ... it gives me a login screen with a count-down. as soon as it's finished counting down, it starts to load a desktop, freezes, the monitor flickers a little bit as if it's trying to change resolution ... then it gives the login screen again with the 30 second count-down. this happens non-stop. what's up with this? ... is ubuntu not compable with my hardware?

---

### Post by spiderbatdad on 2007-11-24
not sure what's going on here. The live cd should not present a login screen. Have you already installed Ubuntu? What type of computer specs?

---

### Post by meindian523 on 2007-11-24
OP doesn't mean login screen,he's talking about the screen with the options like Start/Install Ubuntu,Boot from Hard Disk,No ACPI,etc IMHO

---

### Post by sober2007 on 2007-11-24
AMD 3800 dual core ... 512 ram, 40 gig HD

i put the CD in ... it said (run or install) ... i clicked that which is the first option available ... i waited a few minutes and then i get a login screen saying wait 30 seconds and you will be logged in as ubuntu ... then my problem happens ... i haven't done anything more than this.

i powered the PC down and back up again and went through the process all over again ... it happens all over again. either the CD is damaged or i have some bad hardware configurations.

if you guys aren't sure, no problem.

---

### Post by spiderbatdad on 2007-11-24
check the Installation forum for better help, potentially

---

### Post by sober2007 on 2007-11-24
meindian523 ... actually, no ... no install options.

to tell you the truth ... when it's flickering back and forth between the login screen and the ubuntu desktop, i do see icons ... one icon says (install) ... i only see this for a split second sometimes before the login screen pops up again with a 30 second count-down. i've never been as far along with ubuntu as you might think. i've never seen so many options before, meandian523

---

### Post by meindian523 on 2007-11-24
try checking the CD.....last option in the screen which has the 30 second countdown and run/install,etc options...

+1 for trying the installation help section.

---

### Post by meindian523 on 2007-11-24
sober2007:

Didn't get the meaning,could you post a screenshot or better explain it?

edit: Does it tell you to input a username or password?

---

### Post by spiderbatdad on 2007-11-24
still don't know much about the computer. Is it an HP?

---

### Post by sober2007 on 2007-11-24
i built my own PC ... running windows XP ... i took out the HD and put in a fresh HD.

i put in my Ubuntu CD and boot from CD ... it gives me some options (checking CD is the last option and i will try this now)

i pick the first option and wait 2 minutes and i'm not presented with any desktop ... i'm presented with a login screen. there's what's like a start menu at the bottom left corner of the screen with reset and shut down options ... it's asking for a username and password at the login screen with a message saying i'm going to be logged in within 30 seconds. after 30 seconds, i hear this jungle music playing and i see wallpaper and desktop icons for a second ... then my screen turns black and my monitor starts to make clicking sounds as if ubuntu is trying to change the resolution of my monitor. my monitor clicks 2 times while it's black and when it's finished i have the login screen again.

i'm wondering if i have a malfunctioning input device ... maybe Ubuntu thinks i'm holding down some keyboard option ... i've never used ubuntu before.

---

### Post by meindian523 on 2007-11-24
sober2007:Please refer this page and tell us which of the images in section 1.2 are you referring to?

[http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon](http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon)

---

### Post by spiderbatdad on 2007-11-24
try this:
at the boot screen hit F6
then you should see options at the bottom of the screen ending with the words "quiet splash --

replace quiet splash --
with
no splash noapic noacpi --

sometimes just no splash nolapic --

notice the difference between noapic and nolapic

---

### Post by sober2007 on 2007-11-24
ha ha ... ok...

i see this screen:
[http://images.howtoforge.com/images/gutsy_desktop/big/pic2.jpg](http://images.howtoforge.com/images/gutsy_desktop/big/pic2.jpg)

after this, i get this screen:
[http://images.howtoforge.com/images/gutsy_desktop/big/pic18.jpg](http://images.howtoforge.com/images/gutsy_desktop/big/pic18.jpg)

the login screen says i will be logged in as "ubuntu" in 30 seconds ... at the bottom of the screen it says:
ubuntu // time

after 30 seconds, the desktop starts to load but then it goes back to the login screen with 10 second count-down ... and then the desktop starts to load and it goes back to the login screen with 10 second count-down ... etc...

---

### Post by meindian523 on 2007-11-24
well,you have reached the desktop but the live CD doesn't normally present any login screen.......

---

### Post by spiderbatdad on 2007-11-24
try this:
hit F6 at the boot screen
this should open options for you.
look for "quiet splash --" at the end
replace quiet splash --
with
no splash noapic noacpi --

sometimes just use
no splash nolapic --

notice the difference between noapic and nolapic

---

### Post by meindian523 on 2007-11-24
well,you have a peculiar case....please give results of checking the Live CD..

---

