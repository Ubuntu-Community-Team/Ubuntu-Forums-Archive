---
title: "Resolution problems while installing Dappa"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by NJD on 2006-06-06
Hi,

since the recent crash of my windows XP system i have decided to become a Linux user, an idea i have dabbled with for a long time.

i have downloaded and run the Dappa desktop .ISO and begun the install process.

when i was taken to the initial LiveCD version that begins before any Hard disk install options i attempted to continue the install only to find the resolution was too low to see all of the install GUI.

i tried to edit the res through gnome but the low option was the only one avalible.

i class myself as an advanced windows user (for what it's worth here) but i know squat about linux other than the bare basics, this is my first leap into it!

i'm running an Elite K7S5A mother board with a Geforce2 MX graphics card. i attempted to use the NVIDIA driver .run file from the NVIDIA website in the terminal but it said 'must be run as root' or something similar.

can anyone please give me some advice as to what i can do to alter the screen res and install this impressive bit of kit?

many thanks in advance for any help you can provide

Regards,

Nathan.

---

### Post by Nano Geek on 2006-06-06
First, welcome to Linux! (By the way, it's Dapper):wink: You can try to run **sudo dpkg-reconfigure xserver-xorg** in the command line. It will try to configure your graphics card for you. If you want to install your driver try what you did before but type **sudo** before it, this will tell Linux that you want to run this command as [Super-User]("https://wiki.ubuntu.com/RootSudo?action=show&redirect=Sudo").

---

### Post by NJD on 2006-06-07
Oops, yes, Dapper sorry. thanks for the advice!! i'll try those out now. ;)

---

### Post by NJD on 2006-06-07
I think my problem may be a monitor one because all the alternative res’s are in the xorg.conf under the graphics card, I think your idea is the best because I can’t seem to edit the xorg.conf manually on the LiveCD part before the install :-S. I’ve found the res and refresh for it so I’ll try that. Does anyone think I’m barking up the wrong tree? I’m really running more off of intuition than knowledge and trying to sponge as much info up from the net as I can!!

Will I need to cntrl alt backspace once I’ve chainged said settings?

Thanks again in advance!!

---

### Post by carlosqueso on 2006-06-07
Yes you will need to ctrl-alt-backspace once you've finished.  If that still doesn't work, try the alternate CD, which has a text-based installer that should work better.

---

### Post by NJD on 2006-06-07
Thanks for all the help here!! i am now writing this from a fully connected linux box for the first time ever!!!

thanks again, you're credits to yourselves!!

Nathan.

---

