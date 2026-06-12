---
title: "Thank you, from a beginner"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by Nevulus on 2007-09-20
I cannot thank enough how great of a experience I've had on Ubuntu. I am a novice linux user, programmer. I decided to set up my own linux box for development and have had an amazing time and learning experience. The help I've gotten from the forums has been an immense resource. At first I was hesitant after an awkward linux experience 3 years ago with red hat and Debian, but setting up Ubuntu fiesty 7.0.4 has been smooth. I ran into a few bumps trying to get my nvidia card to run at native resolution but it was an incredible learning experience. Eventually I got it running perfect. Now as for CF, I never got it running at all but Beryl is great, and runs so smooth.

My next step was setting up LAMP. I was worried I would have a few weeks of troubleshooting to get it working correctly but with one simple click thru synaptic manager, and everything was installed and fully functional in seconds. Now phpmyadmin is another story heh. Overall I'd like to thank everyone, while I have not posted ever on this forum, it is because I've found answers to all my problems after a little elbow grease and site searching :)

**Now that i finished my simple rant & rave I can move on to my few questions:**
1) Are there any resources online for server security for a n00b?
2) After upgrading my kernal, in the GRUB menu it lists 2 kernals, is there anyway i can disable the old version? delete it?
3) When going to System>Preferences>Hardware Information none of my hardware is listed on there? I see my intel core duos listed twice, and all the categories are there, but none of the vendor info for my parts. Is this normal?
4) After installing LAMP I was informed by various people that running a GUI/Xwin and a server will cause heavy lag, should i reinstall just a basic LAMP service with no gui/gnome/kde/etc and have a seperate box as a host server? If so should I be looking at specific hard-drives? Please direct me to the appropriate resources for n00b server setting up :confused:

---

### Post by Mud.Knee.Havoc on 2007-09-20
Somebody probably already beat me to it (I took my sweet time answering this), but here goes.

1. Here's a good place to start for learning about server security: [Ubuntu Forums Server Security]("http://ubuntuforums.org/showthread.php?t=510812").  There are a couple things you'll probably want to do right away, such as using keys instead of passwords for SSH and stuff like that.

2. You can edit your menu.lst and get [rid of older entries ]("http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/")that you don't want to appear.  

3. Somebody else can help you with that. Sorry! :)

4. I used to run a server and never felt the need to put a GUI on it.  It's so much easier to just power it on, stick it in a corner somewhere and forget about it.  SSH in whenever you need to, or use webmin or something like that to take care of stuff remotely if you don't want to do it by hand.  I used a separate box as a server... it was a Pentium that I rescued from the trash, 500 MHz that I ran at 250 MHz to keep power consumption down, stuck in 192MB of memory, and I was off to the races. :D  If you're doing something serious with it, maybe you'll want to worry about the hard drive.  If you just want to stick a blog and a few websites on there, just grab the closest hard drive you can and put it in there.  I think I used a 10 gig drive, which was about 9.5 gig empty. :P

---

### Post by Pumalite on 2007-09-20
Not a good idea to delete an old kernel; you might end up having nothing to boot from after an update or upgrade. Better to keep them unless you run out of space.(comment them out in menu.lst)

---

### Post by kellemes on 2007-09-20
> **Pumalite said:**
> Not a good idea to delete an old kernel; you might end up having nothing to boot from after an update or upgrade. Better to keep them unless you run out of space.

Good point..
It's the power you have with GNU/Linux to have as much kernels as you want. I always have 2 or 3 kernels to boot with in case of trouble.

---

