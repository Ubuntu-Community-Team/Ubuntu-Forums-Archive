---
title: "Could not log in!"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by koosfoto.hu on 2007-05-05
Greetings,

I have Ubuntu since only some days... and Windows is dead, so this is my only system now.

This morning, when I started my PC, I gave 3 times my user name and password to Ubuntu... it seemed to accept them, started, played the music, showed the normal desktop, without the right side elements (time and log out)... and returned to prompt me for the user name!
After 3 times, I restarted the PC.
Same thing.
I logged in with another username, who is a simple user fro Ubuntu... and I got in!
So, I asked Ubuntu to switch user... and I am in, with my normal, admin account.
Woww... this was fearful! 

What is this? How can I avoid this to happen again? 
And, if it happens, so I cannot log in... what can I do????


Thanks, and greetings,

Tamas

---

### Post by akudewan on 2007-05-05
It doesn't look like an authentication problem to me. More like a problem with Gnome or gdm. If it happens again, try going to a console (Ctrl+Alt+F1) and login from there.

---

### Post by koosfoto.hu on 2007-05-05
Thanks, akudewan!

You mean, that when I am prompted for the username, I should go to a console (Ctrl+Alt+F1)?
And there? 
Please, note, I am very new in Ubuntu... and I do not the console, neither.... 
So, if I see the console, what should I do?

And, I think, it is rather not normal! I mean, it must be a bug, a problem, something what should not happen... is there a way to correct it?

How can I find the problem and correct it?

What should I do with the Gnome? 
What gdm is? And what to do with it?

(Sorry, if I ask too basic questions... this is the level I am at...)

Greetings to all,

Tamas

---

### Post by akudewan on 2007-05-05
Hi,

If this happened only once, and did not repeat, then you can ignore it. It's most likely a bug. If it repeats, then you can login from the console as I described (Ctrl+Alt+F1), This is the text mode, you won't have any windows here. Logging in, you can run commands to see whats wrong with your system. (I won't elaborate on this right now, since you're a newbie) :) 

An easier option is to select "Gnome-failsafe" from the login screen.

Gnome is the default window manager that comes with Ubuntu. There are others also, like KDE, XFCE, window-maker etc.

gdm is the screen that allows you to login into Gnome. Again, there are others like Kdm and Xdm.

---

### Post by koosfoto.hu on 2007-05-05
Thanks, akudewan!

It did happen again, when I wanted to log in!
And I entered the same way, as I did before: logged in with another username... it worked... than I switched user to my normal, admin name, and here I am , in again!

How can I correct this in my system? Or in Gnome?

If it is a bug, what should I do?

Thanks,

Tamas

---

### Post by akudewan on 2007-05-06
Try logging in  using gnome-failsafe. The option will be available from gdm where you login.

Are you using compiz or beryl ?

---

### Post by koosfoto.hu on 2007-05-06
Hi akudewan!

Sorry, I do not know what compiz or beryl are... 

I used your advise - Thanks! I Logged in with the safe mode... 

I was using the Top Panel in 60 pxl size. I thought - when I saw, how the system builds itself up - that this might cause trouble for Gnome... So, I changed it to smaller, to 44. So, the time is displayed in one row, instead of two (with the 60 pxl).
Guess what?
Now I can log in normally!

So, I think, there is a bug... what one may be able to reproduce! So, it could be corrected, I think.

Thanks for your help!
And... how can we report this bug for correction? Is reporting a bug a kind of contribution to Ubuntu? I would like to add something in, myself, as well... 

(I use a solid color panel background, as well...)

Greetings,

Tamas

---

