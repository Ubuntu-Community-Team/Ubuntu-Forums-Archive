---
title: "Ubuntu beginner needs help!!"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-06-11
I am a new Linux convert from Helldows XP(lol)  I have decided to go with the Ubuntu distribution because it seemed the most user friendly for beginners. I attempted to download the newest version of Ubuntu (feisty) several times, from different mirrors.  I even tried using 2 different burners at 1x speed to ensure that the burning went smoothly.  I used MD5SUM to check the validity of the Iso image, and everything checked out.  But, for some reason, every time i tried to install Ubuntu on my system it would not work.  I found an older version of Ubuntu at work (v 5.04) and decided to install the older version on my machine and go through the updater to eventually arrive with the current version(feisty).  The install was successful.  When i tried to update through the GUI, it prompted me to input the "root password".  During the install i was prompted to input my user password, but no root password.  Is there a default root password? Is there a way to update without being prompted to input a root password?  Please help!!

---

### Post by taurus on 2007-06-11
What is the spec of your machine?  Also, what is the error message on the screen when you try to install Feisty?

---

### Post by reckless2k2 on 2007-06-11
Well unless you created a root password the "password" should be your password for your user. If it's not, then do the following:

$sudo passwd root

Then you'll be asked your current password for sudo then the password creation for root will begin. Some people would not suggest this but it might seem that somewhere along the way you created a root. Not sure. 

Try your sudo password first and see if that gets the update going fine which it should.

---

### Post by ITdrummer on 2007-06-11
Well it is an old Dell Optiplex with a Pentium III, 512MB ram, everything else is stock dell hardware. I already have a dell laptop that i use primarily, i just wanted to play around without Linux without fear of destroying my current, working machine.  The error message i was receiving when trying to install feisty was "invalid or corrupt kernel image".  I visited the forums and many people had suggested: 1) burning at the slowest speed and 2) downloading from a different mirror or trying to download from a torrent file.  I tried all of these methods, but no luck.  

> **reckless2k2 said:**
> Well unless you created a root password the "password" should be your password for your user.   Ive tried entering the password i used during install, but it says wrong password.

---

### Post by freesitebuilder on 2007-06-11
This site has a good explanation of security and passwords [http://www.whylinuxisbetter.net/](http://www.whylinuxisbetter.net/) - choose the "Linux protects your computer" section.

---

### Post by ITdrummer on 2007-06-11
> **freesitebuilder said:**
> This site has a good explanation of security and passwords [http://www.whylinuxisbetter.net/](http://www.whylinuxisbetter.net/) - choose the "Linux protects your computer" section.

thank you for the website but....this has nothing to do with my post.

---

### Post by reckless2k2 on 2007-06-13
Did you try the command I suggested?

sudo passwd root?

That "should" allow you to create a root password.

---

