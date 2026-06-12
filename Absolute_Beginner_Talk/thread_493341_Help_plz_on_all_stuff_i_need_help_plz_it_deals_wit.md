---
title: "Help plz on all stuff i need help plz it deals with the installation of ubuntu"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Korea91 on 2007-07-05
ok im trying to install ubuntu 7.04 the desktop version on my sony vaio VGC-VA11G desktop
ATI MOBILITY RADEON X700
yet when i put cd in and reboot and say install it trys and then goes blank
when i do the safe grafics mode it says x server is wrong and so i tried the sudo dpkg-reconfigure xserver-xorg
but i was so confused with it i didnt no wat to do 
wats wrong with my computer ahhh
it would be very much abliged for any help i really wanna try ubuntu oh and my operating system now is media center XP

---

### Post by Happy_Man on 2007-07-05
Great, when you put in ```
dpkg-reconfigure xserver-xorg
``` you did the right thing. Now, just keep pressing enter until you get to a screen full of drivers. Scroll to select "vesa", spacebar to select, keep hitting enter until it drops you back to a prompt. Now enter ```
sudo /etc/init.d/gdm start
``` and cross your fingers!

---

### Post by Korea91 on 2007-07-05
thx for the help but it didnt work when i put in code it says failed
and then i put it in a second time it brings me back to the page about the xserver not working

---

### Post by snwbord2456 on 2007-07-05
I just got ubuntu today also and have been having problems, I had the same issue, you need to use the alternate ISO, its a checkbox on the main download page. Its because you have an ATI videocard.

---

### Post by Happy_Man on 2007-07-06
> **snwbord2456 said:**
> I just got ubuntu today also and have been having problems, I had the same issue, you need to use the alternate ISO, its a checkbox on the main download page. Its because you have an ATI videocard.
I didn't want to suggest that, but yes, that seems to be your only option at this point. Don't worry, it's not as bad as they make it out to be.

---

### Post by Raineer on 2007-07-06
> **Korea91 said:**
> thx for the help but it didnt work when i put in code it says failed
and then i put it in a second time it brings me back to the page about the xserver not working

You really need to be more specific, when you put in what code and I am sure it said more than "failed", are you saying that "gdm" didn't start?

Really, proper English and details will get you up and running MUCH faster than you realize, please try to provide them. Don't expect too many responses with 2 "plzs" in the topic header.

---

