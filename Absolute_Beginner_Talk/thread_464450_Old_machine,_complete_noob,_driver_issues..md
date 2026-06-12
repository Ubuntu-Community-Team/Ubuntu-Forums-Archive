---
title: "Old machine, complete noob, driver issues."
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by CaptainArD on 2007-06-04
The machine:  
AMD duron clocked at 780 MHz
768 Mb RAM
8 gig HD
eGeForce 2 MX 400
generic network card, not sure of brand.
Kubuntu 7.04

I'm completely new to linux. I got this computer for free by piecing it together from other trashed computers, so i decided to try linux out for a while. I have learned a little in the last few hours i have been trying to get it to work. But after trying to get the thing to boot correctly and sort our hardware issues, i have lost patience trying to muddle out how to install things. 

I really just want to install the drivers for my card. The card is not supported by the repository, far as i can tell, so i have to use the legacy drivers from nVidia.  I have this file as a .run and am trying to figure out how to install it. If i understand correctly, in Ubuntu you do not need to be root to install. I have tried using the command prompt to install by typing "sudo sh *name of driver file.run*" but the console tells me that the file cannot be run/executed or whatever.  I have tried doing this both through Konsole and by pressing ctrl+alt+f1.  To the best of my knowledge, i did everything right, so i am at a comlete loss. Can anyone help me/ refer me to some really simple instructions? Google did me no good.

Another issue is Wine. It looks like it's installed on this machine, as i can opt to remove it through the package manager. However, I don't see it anywhere, nor is it a choice for me to use to run windows apps. How do i use this/ get ahold of this to install?

and the clincher... i have no internet on this machine, so i cannot download updates or files directly. makes everything harder.

Thank you all for your help and patience. I'm sure helping noobs gets frustrating.

---

### Post by taurus on 2007-06-04
1.  What is the name of the file that you want to install?  For now, use nv driver for your graphic card until you get it up and running.  Then, install an nVidia driver for it.

2.  As far as I know, wine is not installed on your machine by default.  And if you want to remove it, try something like

```
sudo apt-get --purge remove wine
```

3.  To find out what ethernet card you have, run

```
lspci
```

---

### Post by shae on 2007-06-04
To use wine, you must use the following in terminal.  After you have it set up you can make a launcher to run that for yourself.
```
wine [path to exe] 
```

Are you unable to use your linux computer's network card or do you not have a router?  Ubuntu might not be the wisest choice if you plan on using it on a computer without internet access.

---

### Post by CaptainArD on 2007-06-05
Thanls for the help, i figured out that i wasn't changing directories correctly. Stupid mistake on my part.  Now i just need to get the header files and whatnot to install.  

There is no router to plug the computer into, which is why i have no internet. When i go back to school it will though, so i wanted to stick to Ubuntu. It will mainly just be a project box, maybe make a emulating machine or a media player, so internet is not the most imoprtant thing just yet.

thanks again for teh help, looking foreward to becoming a linux user.

---

