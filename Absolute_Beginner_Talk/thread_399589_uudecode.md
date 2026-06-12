---
title: "uudecode??"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Zargon2000 on 2007-04-02
Please help!  Newly installed Ubunto (I really want to try this out!), and trying to get internet connection.  If I can get an internet connection, I won't have to keep booting back and forth from WinXP to Ubunto to ask you guys for help!  :-)  I downloaded the drivers for my wifi card (madwifi-base-1_2_1b) and am trying to install them.  I tried using Synaptic, but can't get it to do anything with the files I have.  From what I understand, they aren't a "package" so that is why Synaptic won't work.  I run the aptitude install command and I get an error that uudecode command is unknown or can't be found.  Is uudecode part of the system or do I need to install it?  Also, there are a lot of directories in the madwifi directory (ath, hal, include and more) that have makefile files in them, along with a bunch of files with the .c and .h extension on them.  What do I need to do to get the uudecode to work and/or install these files??  Thanks a bunch form a newbie XP to Linux user!!

I have the output from the make and make install commands attached.

---

### Post by sujith_m82 on 2007-04-06
You have to install sharutils.

Type this in a terminal :
"sudo apt-get install sharutils"

---

