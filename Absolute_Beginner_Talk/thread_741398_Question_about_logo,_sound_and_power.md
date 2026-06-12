---
title: "Question about logo, sound and power"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by nadanil on 2008-03-31
Hello,
Well I made the switch from XP. I got tired of that little annoying pop-up that always told me "Your Computer May Not Be Safe!" So I just trashed the whole thing and moved onto linux. Take that XP.

--------------
Specs incase you need them:

DELL INSPIRON 6000, 1GB RAM, PENTIUM M 1.6 GHZ, INTEL 2195 ABG, UBUNTU 7.10
-------------
There are a few problems that I am having, in a list:
1) How can I get the default title bar back (The top one with the menu/date/usr/etc)? I deleted somethings (like network and someother stuff) and I really want the default back.

2)How can I get a splash screen to show when I start up, instead of staring at a black screen for 3 minutes.

4) On my laptop there are lights to show when the killswitch are on/off for bluetooth and wireless. On XP these lights lit up when wireless/bluetooth was on, and turned off when they were off. But on ubuntu I can't figure out how to make them correspond. It'd be nice so that I could know if I'm saving as much battery as possible when on the go.

5) On my laptop there are some dedicated media buttons upfront (for sound up/down, mute etc). They used to work, but I obviously did something, and now they don't. When I press sound up/down/mute a little pop up screen shows up saying that sound is going up/down/mute but it does nothing in reality. I have no idea what I did (but I do know that I was playing around with the soundcard options under sound preferences and that I installed alot of media players because I wanted to get an EQ).

Also I'm just looking for some reference to these issues: 

1)How can I put my laptop to sleep/hibernate? When ever I do it (I've tried every way, closing the lid [when the option to sleep when closed lid was turned on etc], pressing the button and pressing crt-alt-del) it just turns off the screen and nothing more. 

2) I have some power saving options on, like turn off the screen after X minutes. The problem is that sometimes when it turns off, it stays off and I have to reboot. How can I fix that?
---------
I think thats all. Hopefully these teething pains will go away soon. It's only normal anyways, I experienced them when I switched to OS X. Like ubuntu alot so far. Thanks!

---

### Post by Fixman on 2008-03-31
> **nadanil said:**
> Hello,
1) How can I get the default title bar back (The top one with the menu/date/usr/etc)? I deleted somethings (like network and someother stuff) and I really want the default back.

There is no way to get it back automatically, but if you right click and press "add to panel", you can add the things you deleted.

> 
2)How can I get a splash screen to show when I start up, instead of staring at a black screen for 3 minutes.

Open a terminal (applications->accesories->terminal) and write
```
 sudo aptitude install gnome-splashscreen-manager 
```

> 
1)How can I put my laptop to sleep/hibernate? When ever I do it (I've tried every way, closing the lid [when the option to sleep when closed lid was turned on etc], pressing the button and pressing crt-alt-del) it just turns off the screen and nothing more. 

system->quit->hibernate

> 
2) I have some power saving options on, like turn off the screen after X minutes. The problem is 
that sometimes when it turns off, it stays off and I have to reboot. How can I fix that?

system->preferences->power management

---

### Post by sancho panza on 2008-03-31
1) I dont know if you can get the default back, but its really easy to play around with the title bar (its called the panel). Just right click on an empty space in the panel and try all the options to see what you need. You can get the menu, date and a lot more by selecting add to panel.
5) Go to system/prefs/sound and make sure you have PCM selected/highlighted in the default mixer tracks list.

Some of the other issues might be bugs and a dell user would be able to tell u if they have been resolved or not.

---

### Post by nadanil on 2008-04-02
Thanks, to you both. 
The boot up program seems to work, and the sound fix worked perfectly.
I'll head over to the Dell forums for the other questions. 
Thanks,
~Peace

---

