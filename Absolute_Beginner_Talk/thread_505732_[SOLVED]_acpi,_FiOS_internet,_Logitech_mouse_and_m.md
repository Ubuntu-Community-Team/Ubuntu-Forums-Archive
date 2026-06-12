---
title: "[SOLVED] acpi, FiOS internet, Logitech mouse and more to come"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by holyskeleton on 2007-07-20
I just put on feisty on my comp yesterday and havent been able to use it yet. so i'm going to list my problems in the chronological order.

from a perfectly working peaceful windows XP...
1. I put the CD in, restart, boot from CD, install, after a while it crashed saying "critical temperature reached". so I did some google then boot again live with acpi=off.
2. the comp booted but my mouse stopped working. I had to install the OS with keyboard only. 
3. during the install it tried to download some language package from the internet but got stuck (around 83% done) so i skipped it.
4. the OS seems to be installed so I took out the CD then boot the system. during the start-up screen it got stuck. (when the start-up music was playing) and I had to press a key on the keyboard continually to load it. if I stop pressing then it gets stuck again.
5. there's no internet. somehow i got a message saying it has 60 updates waiting to be installed but i cant even go online. however when I boot from the CD without the "acpi=off" thing everything was working include the mouse but not the side buttons. but again it crashes with the temperature thing.
so now i got a comp that nothing works.

my mouse is the 2nd gen logitech G5, internet is verizon FiOS connected directly to the computer.

---

### Post by holyskeleton on 2007-07-21
ok...maybe that was a stupid question. or there was no question mark...anyway lets try it again:

If I have FiOS internet with the router connected directly to my PC, what should I do to make the internet work?

---

### Post by sad_iq on 2007-07-21
Can you ping your router?? Can you **ping -c 3 [www.google.com](www.google.com)**. My connection usually fails when I don't manually put my DNS entry...and it also fails with a dynamic ip(static works ok thou), I think it's the routers fault. The FIOS (ISP I suppose) has nothing to do...just make sure you can ping the router and the outside world!
 About the logitech thing...I don't own one...but there are some guides out there...maybe they can help:
[http://ubuntuforums.org/showthread.php?t=219894&highlight=logitech](http://ubuntuforums.org/showthread.php?t=219894&highlight=logitech)
[http://ubuntuforums.org/showpost.php?p=2461304&postcount=285](http://ubuntuforums.org/showpost.php?p=2461304&postcount=285)
Also go here and look for more guides:
 [http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)
The temperature ...I can't really help you...maybe someone more skilled will give you a hint. Also...what computer do you have??? Laptop??? Post your spec also...it will be easier for us to help if you give us more details!

---

### Post by holyskeleton on 2007-07-22
ok i let my computer cool down for a while then restarted and reinstalled the whole thing. this time is better because it managed to get almost 95% of the installation done before getting the temperature thing again... which it did.

but it's alright because now the internet and the mouse is working (although not the special buttons). yay!

New problem: now the computer randomly shuts down for no good reason. I was just adding the "fish" thing to the top, clicked on it, then something poped up (probably fortune) then the screen went back to DOS in black and white, saying it is starting some modules.

I've noticed on the bottom it saying something about "powernowd" not sure if it matters.
then on the second screen it says **"doing wacom setup"**???

I'm using a 4 yr-old eMachines T 2040 desktop. and I managed to get all the updates...

and I can probably try some logs but i dont understand them...

---

