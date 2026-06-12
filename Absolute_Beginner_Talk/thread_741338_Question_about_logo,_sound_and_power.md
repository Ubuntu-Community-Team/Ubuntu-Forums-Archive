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

3) How can I put my laptop to sleep/hibernate? When ever I do it (I've tried every way, closing the lid [when the option to sleep when closed lid was turned on etc], pressing the button and pressing crt-alt-del) it just turns off the screen and nothing more. 

4) On my laptop there are lights to show when the killswitch are on/off for bluetooth and wireless. On XP these lights lit up when wireless/bluetooth was on, and turned off when they were off. But on ubuntu I can't figure out how to make them correspond. It'd be nice so that I could know if I'm saving as much battery as possible when on the go.

5) I have some power saving options on, like turn off the screen after X minutes. The problem is that sometimes when it turns off, it stays off and I have to reboot. How can I fix that?

6) On my laptop there are some dedicated media buttons upfront (for sound up/down, mute etc). They used to work, but I obviously did something, and now they don't. When I press sound up/down/mute a little pop up screen shows up saying that sound is going up/down/mute but it does nothing in reality. I have no idea what I did (but I do know that I was playing around with the soundcard options under sound preferences and that I installed alot of media players because I wanted to get an EQ).

I think thats all. Hopefully these teething pains will go away soon. It's only normal anyways, I experienced them when I switched to OS X. Like ubuntu alot so far. Thanks!

---

### Post by jakupl on 2008-03-31
nr. 2.

```
sudo gedit /etc/usplash.conf
```

change from 1280 x 1024 to 1024x768

then:

```
sudo update-usplash-theme usplash-theme-ubuntu
```

try now to reboot. It should also make the boot alot faster :popcorn:

---

### Post by brownknight on 2008-03-31
I have answers for some but not all your questions:

[B]1) How can I get the default title bar back (The top one with the menu/date/usr/etc)? I deleted somethings (like network and someother stuff) and I really want the default back.
[/B]
Is the title bar (panel) gone or you just want to add the original icons back? To put the top panel back just go down to the bottom panel, right click and choose New Panel then configure it to go to Top. If you still have the top panel and just want to get the icons back just right click on the panel and choose add to panel. You will see a list of items you can add to the panel.

**2)How can I get a splash screen to show when I start up, instead of staring at a black screen for 3 minutes**.

I have used this program called startupmanager. You can install it from the terminal or synaptic[B]

3) How can I put my laptop to sleep/hibernate? When ever I do it (I've tried every way, closing the lid [when the option to sleep when closed lid was turned on etc], pre[/B]ssing the button and pressing crt-alt-del) it just turns off the screen and nothing more.

This issue of hibernate/suspend is persistent in many systems - it means it is a problem for a lot of us and not only you.

---

