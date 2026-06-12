---
title: "[SOLVED] Unknown Problem?"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by tjwoosta on 2008-01-24
I have been running ubuntu for a few weeks now but other than that i have no experience with linux. 
A few minutes ago i was getting an add on for firefox and it installed and asked me if i wanted to restart firefox so i said yes but nothing happened my system just completely froze up. i held down the power button untill the computer shut down. when i restarted ubuntu the gdm wont start. i tried to start it in recovery mode and it ran a bunch of lines and stoped so i typed sudo /etc/init.d/gdm start  (after i saw it on another post) and still it did not work what the hell did i do  and how do i fix it?  Please help!

---

### Post by Pelham123 on 2008-01-24
Can you give us a little more info?

What happens when you boot up your PC at the moment? Do you get as far as GRUB? Do you get the splash (orange bar) screen? Do you boot into a text based login screen?

---

### Post by tjwoosta on 2008-01-24
i get past the splash screen but not as far as the login
it has a bunch of lines all followed by an ok 
the screen keeps flashing every few seconds

---

### Post by Sef on 2008-01-24
Go into GRUB, and use recovery mode.

(To get into GRUB, just keep pushing esc upon starting.)

Report on if you can get into Ubuntu or not.

---

### Post by tjwoosta on 2008-01-25
i tried already but it didnt do anything do i need to type something?

---

### Post by hyper_ch on 2008-01-25
what error message where you given when you tried to run gdm?

---

### Post by tjwoosta on 2008-01-25
okay there as no error message. i would get to the point where it had a bunch of lines of text all followed by an ok. then the screen would start to flash every few seconds like it was trying to load something but nothing happened. It stayed like this for over ten minutes. i tried to run recovery mode and after all of the text scrolled it came to a stop  and said

tj@tj-laptop:~$ 

here i typed sudo /etc/init.d/gdm start

it said gdm started but nothing happened

so i typed sudo dpkg-reconfigure xserver-xorg

after reconfiguring i typed sudo etc/init.d/gdm start

still nothing happened, so i restarted my computer and ran the regular ubuntu (not recovery mode) and this time it worked

i have no idea what the hell caused the problem but at least now i am back at my desktop

i still am having problems with my display however but that is another thread
 so thank you all for trying to help i do appreciate it

---

