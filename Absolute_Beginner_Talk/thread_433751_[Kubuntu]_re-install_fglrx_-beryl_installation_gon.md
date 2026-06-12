---
title: "[Kubuntu] re-install fglrx? -beryl installation gone bad-"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Prophion on 2007-05-05
Hey, 
I have been using Kubuntu for a few months now but never dared to install beryl on it.. al those warnings really had an effect on me :D 
But then i stumbled on this howto: [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

I read it through a couple of times and it seemed easy enough. Editing the xorg.conf file seemed to be the most daunting part but I had edited it before and that all worked out (eventually).

So i decide to go for it! (I know, I should have known better 8-[ )


I did the first steps (disabling the fglrx kernel module, checking glxinfo and editing xorg.conf) and everything looked ok so far. So I tried restarting X but that didn't work. So now I am stuck on the command line (writing this on my GF's windows-laptop, how painfull) and not sure what to do. 

This is what I have tried so far:
-checking the xorg.conf file and see if I did not make any mistakes: *pretty convinced that it is correct*
-trying to run "glxinfo | grep vendor" (next step in the howto): *Error: unable to open display (null)*
-getting the xorg.conf backup back and undo disabling the fglrx kernel module: *I get a message saying it the fglrx module is not used in the xorg.conf file * :-? 

Some other (important) stuff:
-after I couldn't restart X, I saw this in the howto:
> 
If you have ATI in the output of the previous command, remove the fglrx driver like this (you can do this also if you have SGI in the output - just to go sure):

"sudo apt-get remove xorg-driver-fglrx; sudo apt-get install libgl1-mesa-glx libgl1-mesa-dri" 

At first I thought I did not have to do this because I had no ATI output at the previous command. but then I saw that beside uninstalling the fglrx-driver it installs mesa-drivers. I hoped this was the problem so I tried installing them form the command line: i get a message saying that both mesa-drivers are the newest versions.   (but is it checking the internet?? I am not sure)

-I am using Kubuntu feisty fawn 7.04 with the latest updates
-I have a AMD XP3000+ on a Asus A7n8X-e Deluxe Mainboard
- and a ATi radeon 9800 pro vidcard


The question is: What to do?
Should I continue the howto and hope it all magically starts working at the end?
or
should I reinstall fglrx somehow (gonna need help with that) because if X isn't working now why should it work later?


Anyway, I hope someone can help me out. My GF is laughing in my face because I was stupid enough to start using Linux (and messing with it) whilst i had a perfectly running windows setup AND even more important I have an essay to write. :-P (hows that for timing?)




[EDIT]

I discovered & fixed the problem. Of course I made a mistake in my xorg.conf (again... :oops: )
In my case BusID should be: "PCI: 3: 0: 0"  in stead of " 1: 0: 0" (what it was in the howto)

so I think everyone with the 
>  Error: unable to open display (null) 
after running the command
>  glxinfo 
should double check the "Device" section in xorg.conf

the command "lspci" will give you the correct BusID


[COLOR="Magenta"]*Prophion Loves figuring out linux the hard way*[/COLOR]

---

### Post by overdrank on 2007-05-06
[QUOTE=Prophion;2597290]Hey, 
 
But then i stumbled on this howto: [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

-I have a AMD XP3000+ on a Asus A7n8X-e Deluxe Mainboard
- and a ATi radeon 9800 pro vidcard


The question is: What to do?
Should I continue the howto and hope it all magically starts working at the end?
or
should I reinstall fglrx somehow (gonna need help with that) because if X isn't working now why should it work later?


Hi according to the how to you posted you will have to reconfigure your xorg and add additional info to it so I would say to continue the how to and follow the instruction to the completion. Good luck and I have beryl running on a x300 ati as you see and its great. :)

---

