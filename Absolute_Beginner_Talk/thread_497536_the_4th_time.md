---
title: "the 4th time"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by knotman on 2007-07-10
im trying to get both my monitors working i got a ati radeon 9800xt the monitors are working but are a mirror image ( as in what i do on one monitor it does the same on the other ( twin view? )) i would like to get them to where i can drag a window over to the other monitor 

i tried 4 different ways and had to uninstall ubuntu 4 times then reinstall it now i reinstalled it and did the updates so as you can tell im no scripe writer and i am very new to this so any help to do this the easy way ( yea right)

---

### Post by Pragmatist on 2007-07-10
[https://help.ubuntu.com/community/XineramaHowTo](https://help.ubuntu.com/community/XineramaHowTo)

---

### Post by Sparkster185 on 2007-07-10
You probably need to adjust your Xorg configurations so it knows to give you the extra real estate.  Using Envy and nVidia settings, this was a breeze for me.  Not sure about ATI.

Have you tried installing/running Envy?

---

### Post by knotman on 2007-07-10
no and that i think is one of the problems is that i dont have any extra programs install one i would like to install is beryl 
i did read that you have to install other programs such as installer helpers and bla bla bla

---

### Post by Sparkster185 on 2007-07-10
I would certainly get your xorg configure properly before trying anything experimental, such as Beryl.  Envy is actually a pretty slick tool, it will download/configure/install the drivers as well as the GUI to the graphics card settings (for nVidia, at least).

[http://albertomilone.com/wordpress/?p=68](http://albertomilone.com/wordpress/?p=68)

---

### Post by knotman on 2007-07-10
yes im thinking that also that is why i what to fix the monitor issues but it seems that every time i go into the xconf i mess something up ,get sick and tired then reinstall

---

### Post by knotman on 2007-07-10
well i managed to mess up the mouse and cant get it to move so for the fifth time im going to uninstall and reinstall and if i dont get it working again im going to delete it and throw out the cd i getting to frustrated trying to get this program working

---

### Post by regomodo on 2007-07-10
4th time? Pah thats nothing. In my first 2weeks must have been 10times. Lost count how many times now.

Your mouse issue can easily be solved. You've been messing with the xorg.conf file

ctrl+alt+F2

login, and type

sudo dpkg-reconfigure xserver-xorg

You are making backups right? Say, if you save the original as xorg_backup.conf you can (when in tty2) open it and save it as xorg.conf. Then ctrl+alt+backspace and your back to where you started

---

### Post by AlexenderReez on 2007-07-10
i don't really understand what is the problem ....hm......is it problem with your resolution or...mouse...or card or graphic card driver.....please clear your problem...and don't mess up your post with unnecessary  information....

back then...i have experienced more than 10 times to install ubuntu for my first time...reason.. at that time,i think it is like windows....no need to refer or ask any where....but i'm glad i stay till today....

---

### Post by knotman on 2007-07-10
> **regomodo said:**
> 4th time? Pah thats nothing. In my first 2weeks must have been 10times. Lost count how many times now.

Your mouse issue can easily be solved. You've been messing with the xorg.conf file

ctrl+alt+F2

login, and type

sudo dpkg-reconfigure xserver-xorg

You are making backups right? Say, if you save the original as xorg_backup.conf you can (when in tty2) open it and save it as xorg.conf. Then ctrl+alt+backspace and your back to where you started

i thought i did but i guess not but every time i go into the sudo i mess something up

---

### Post by knotman on 2007-07-10
> **reez0105 said:**
> i don't really understand what is the problem ....hm......is it problem with your resolution or...mouse...or card or graphic card driver.....please clear your problem...and don't mess up your post with unnecessary  information....

back then...i have experienced more than 10 times to install ubuntu for my first time...reason.. at that time,i think it is like windows....no need to refer or ask any where....but i'm glad i stay till today....

what i am trying to do is get the muilti monitor  working right right now i got the same stuff on the other monitor i.e. what ever i do on one monitor it does the same on the other
the mouse is fine untill i go into sudo to configur the ati disply i just click ok to bypass the mouse and that is where i mess that up

---

### Post by knotman on 2007-07-10
[QUOTE=regomodo;2996958]4th time? Pah thats nothing. In my first 2weeks must have been 10times. Lost count how many times now.

ok i`ll keep trying my 5 times seems like nothing now i thought it was just me i can ripe a puter apart and put it back together but as for the programming i sux this is why and how i mess stuff up in the sudo

---

### Post by Pragmatist on 2007-07-10
If your hardware works with Linux, then you can solve these problems.  The best way is to approach the problems one-at-a-time, methodically, and to have patience.  Let's get organized!

Give us a list of your problems. Include:
         (a) **What you are trying to do** (this is most important.  Sometimes people ask how to perform some diagnostic procedure, but don't explain why they are diagnosing in the first place.  It is better to explain what your goal is, and let those who are helping you decide which approach to use to accomplish it.)
         (b) Relevant information.  This includes configuration files, log files, hardware information, etc...
         (c) What you have tried already.

Read some general troubleshooting guides.  These will help you to ask better questions and, consequently, receive better answers.  There is one such guide linked from my signature, but there are many others too.

---

### Post by knotman on 2007-07-10
ok reinstalled dling updates now 

what i am trying to do is get the muilti monitor working right right now i got the same stuff on the other monitor i.e. what ever i do on one monitor it does the same on the other i

---

### Post by Pragmatist on 2007-07-10
> **knotman said:**
> ok reinstalled dling updates now 

what i am trying to do is get the muilti monitor working right right now i got the same stuff on the other monitor i.e. what ever i do on one monitor it does the same on the other i

Have you tried Xinerama??

---

### Post by knotman on 2007-07-10
no i didn`t i just install envy and installed the ati drivers but now i got an error message
error:brokencount>0

i guess i`ll download Xinerama and try that

---

### Post by knotman on 2007-07-10
i could not find the Xinerama program but i did some how get the ati catylas going it will see both my monitors and display them both but i still cant change the settings i,e, drag a window to the other monitor nor make one big screen

---

### Post by Pragmatist on 2007-07-10
> **knotman said:**
> i could not find the Xinerama program Try these instructions:
[http://www.paralipsis.org/2006/01/enabling-xinerama-in-ubuntu/](http://www.paralipsis.org/2006/01/enabling-xinerama-in-ubuntu/)

 > **knotman said:**
> but i did some how get the ati catylas going
What is "ati catylas"?

---

### Post by knotman on 2007-07-10
What is "ati catylas"?[/QUOTE]

it is the control panel for my ati 9800xt video card it allows me to change the setting in there it will show my monitors and it displays them as monitor 1 and monitor 2 but i still have the same problem

---

### Post by regomodo on 2007-07-10
i'd go with what pragmatist said. As i said, i got so frustrated in my 1st month of ubuntu that i gave up, for a week. I thought, sod it, give it another bash and solve 1 bit at a time.

Saying all that i rarely use ubuntu on my pc as i can't do jack with it, but i use it exclusively for my lappy.

---

