---
title: "Help! Feisty won't start anymore"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by jnewm on 2007-08-25
Just about 30 minutes ago, I installed some updates.  I logged out because OpenOffice wasn't starting for some reason, but when I tried to log back in I just got the little white spinning thinking wheel on an otherwise black screen.

When I try to reboot, the same thing happens.  I see the "Ubuntu" loading screen (with the orange bar), then I just get a black screen with the little white spinning wheel, which then flashes and returns to the same thing, which then stays on the screen, spinning and spinning, but not doing anything - i.e. no log in screen ever.

I tried booting in recovery mode, but when I hit <ctrl+D> same thing happens as above, and when I go into the command prompt, I really have no idea what to do.

The only thing other than updating I can think of, is that I recently installed compiz fusion.  But compiz fusion was working fine before.  Anyway, any help would be much appreciated because i can't use Ubuntu on my computer at all now!

Thanks!

---

### Post by jnewm on 2007-08-25
Anybody?  Please?  I just can't get to the login screen, the damn spinny wheel just spins and spins...  I can press <ctrl+alt+F1> and mess around in the command prompt, and I can type <startx> and get to the graphical interface.  But I can't get to my regular login!  I'm sure I screwed something up with compiz fusion, unless it was the new updates.

](*,)

---

### Post by scrooge_74 on 2007-08-25
Hi,

sorry to hear you are having this kinds of problems.  I may not be able to help you fix it, but I can give you some pointers.  

First next time something gets slow or stops respoding, you are better of killing the app than just loggin you.  You can either use the resource manager and kill it or from the command line type ps -ax, find the app giving you trouble and check the number to the side then type kill -9 (number of the app)

As for your problem.  I suggest you boot the system, then press CTRL+ALT+F1

that will take you to a command prompt, if you can log in that means the problem is with one of your gnome config files in your /home folder.

You can then type the following  rm -rf .gnome .gnome2 .gconf .gconfd .metacity

I got this from [here]("http://linuxfud.wordpress.com/2006/09/29/ubuntu-crashes-on-start-and-returns-to-the-login-screen/")

Probably something got stuck either in the Gnome config files or with compiz for sure

---

### Post by AceofSpades19 on 2007-08-25
try this
sudo /etc/init.d/gdm start
at the command prompt

---

### Post by jnewm on 2007-08-25
Thanks so much for the replies.  I actually just figured out what it was after a ton of random searching.  I'd completely forgotten that I'd been messing with the login windows, and apparently accidentally checked the "Enable Accessible Login" option.  After following the instructions in this thread:
[http://ubuntuforums.org/showthread.php?t=458419](http://ubuntuforums.org/showthread.php?t=458419)
everything is working again.
But thanks for the help anyway
PS Actually while I have some more experienced attention, any advice on how to fix what I did trying to fix the OG problem?  I did the whole <dpkg-reconfigure xserver-xorg> thing, and now all my screen resolution settings are pretty awful.  Previously, my settings were just based on whatever Ubuntu discovered at install.  Is there any way to have Ubuntu just rediscover and do everything automatically again, with regard to screen settings? Thanks again!

---

### Post by scrooge_74 on 2007-08-25
do the dpkg reconfigure again and be carefull with the replies, you have to correctly select the resolution and other things

---

### Post by pgar23 on 2007-08-25
Im glad you got this problem resolved. Can you mark this thread as solved for other people who have this problem can check it. Go to top of page>thread tools>mark thread as solved.

---

