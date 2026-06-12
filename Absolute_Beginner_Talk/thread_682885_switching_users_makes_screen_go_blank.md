---
title: "switching users makes screen go blank"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by oisuxx on 2008-01-30
ive been getting a blank screen when i switch users in ubuntu 7.10
me and my girlfriend share the pc, but we have our own logins. is there a way to fix this? when we log the other out, THEN log in its not an issue. but if we switch users it goes blank and we have to press ctrl+alt+backspace 2 times.

---

### Post by monte48lowes on 2008-01-30
If you have compiz running using XGL there are problems with starting an additional xsession for another user. 

Mike

---

### Post by oisuxx on 2008-01-30
XGL?
i do have compiz fusion running.so if i turn off that then switching will be fine?

or is there some fix for it?
cause i like my bells and whistles! :D

---

### Post by monte48lowes on 2008-01-30
If you are using an Nvidia graphics card you do not need to use XGL for compiz. If you are using an ATI graphics card you will need to use XGL for compiz. What graphics card do you have?

Mike

---

### Post by oisuxx on 2008-01-30
its an nvidia
i forget the exact model.

---

### Post by clarknova on 2008-03-13
And how does one disable xgl? My compiz experience is very simple to configure: Sytem->Administration->Appearance->Visual Effects. I'm using the "Normal" setting and getting a blank screen (except a functional mouse pointer) when switching from the second login to the first, but not from the first to the second.

ps, when I'm staring at the blank screen I can enter the password of the first login to get back to the desktop. Minor annoyance, therefore, but still a problem, no?

I'm using an onboard nvidia quadro 210s/6150LE/nforce 430 gpu. This issue exists in nvidia driver version 169.12, 169.07, and in the default gutsy restricted driver (IIRC).

db

---

### Post by dastasha on 2008-03-15
I'm having the same problem. The difference here is that I'm not using any visual effects, however I am using the restricted Nvidia drivers. I have these enabled for the first user but I cant figure out how to enable the drivers for the second user. No option appears under System/Preferences or Admin. :confused:

I had not discovered that you could enter the first users password from the blank screen - I shall try that. I should try the ctrl - alt - backspace trick as well -

---

### Post by louieb on 2008-03-15
What I've found when the screen goes blank press Ctrl+Alt+F7 this will take you back to the 1st user. 
Then press Ctrl+Alt+F8 this will take you back to the 2nd user and the GUI will start working.

I think in has something to do with Gnome. When I switch to the second user and that user is using fluxbox I don't have the blank screen problem.

---

### Post by clarknova on 2008-03-17
> the restricted Nvidia drivers. I have these enabled for the first user but I cant figure out how to enable the drivers for the second user

When you enable any video driver, restriced nvidia driver included, it is enabled on the xserver. In other words, if you're using the restricted driver for one user account then you're using it for all. You should see the nvidia splash screen right before the login screen comes up before logging in, for all users (unless the splash screen has been disabled, but it's on by default).

> What I've found when the screen goes blank press Ctrl+Alt+F7 this will take you back to the 1st user.
Then press Ctrl+Alt+F8 this will take you back to the 2nd user and the GUI will start working.

On my machine ctrl-alt-f7 takes me to the first user and ctrl-alt-f9 takes me to the second user. ctrl-alt-f8 takes me to a logging console.

Anyway, I was getting the white screen only when switching to ctrl-alt-f7 (always user "A") but not on f9 (was always user "B"). Then I had some other issues with user B, so I created user C and migrated B's files and started logging into f9 as user C. Then I was geting the blank screen on both f7 and f9 (users A and C). Then after a day or two I stopped getting the blank screen on f9, but still getting it on f7. Confused? Me too.

db

---

