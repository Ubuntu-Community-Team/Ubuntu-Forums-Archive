---
title: "NVIDIA Attempt Causes Wireless to fail"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by GSF1200S on 2007-04-03
So I try to install my NVIDIA drivers like I have been for the last 3 days (about 5-7 hours a day), and in the process my wireless card no longer works.

To be concise, part of the suggestion was uninstalling all traces of NVIDIA using the following commands:

sudo apt-get autoremove nvidia-glx

sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run --uninstall

While these are VIDEO CARD ORIENTED, im guessing some the packages listed as dependencies were uninstalled in the process, apparantly some of which were necessary for my wireless. So, what are all the files/packages required to make my wireless card work? I **think** madwifi is the reason why my wireless worked, but watching the uninstall process (at the prompt, X was closed) I could only see a few ndiswrapper things being removed. What do I need to get it working again?

---

### Post by useResa on 2007-04-03
Your assumption is correct. More information on this issue can be found in an extensive thread [HOWTO: Install the Nvidia driver on Edgy Eft](http://ubuntuforums.org/showthread.php?t=281823) by tseliot.

What could be useful is a tool that tseliot has written to install the latest Nvidia driver, called Envy. You can find more info about this on [his homepage](http://albertomilone.com/nvidia_scripts1.html).
This tool also prevents the issue you are indicating as also indicated on his page
> ENVY does NOT REMOVE your RESTRICTED MODULES ANY MORE. Therefore you can use it even if you connect to the internet using your wireless card.
I have recently switched from installing the Nvidia driver by hand to using Envy and am please with the way it has helped me out.

Hope this may help you too.

---

### Post by GSF1200S on 2007-04-03
> **useResa said:**
> Your assumption is correct. More information on this issue can be found in an extensive thread [HOWTO: Install the Nvidia driver on Edgy Eft](http://ubuntuforums.org/showthread.php?t=281823) by tseliot.

What could be useful is a tool that tseliot has written to install the latest Nvidia driver, called Envy. You can find more info about this on [his homepage](http://albertomilone.com/nvidia_scripts1.html).
This tool also prevents the issue you are indicating as also indicated on his page
.
I have recently switched from installing the Nvidia driver by hand to using Envy and am please with the way it has helped me out.

Hope this may help you too.

Damn, I really wish Envy would work. Im stuck in a paradox- a spiraling world of crapiness if you will. The only way I could get my wireless card to work was my upgrading to Feisty. The only way I can get my video to work (apparently) is to use Edgy and envy. Im screwed. Im already dual booting WinXP, so I guess Id have to go with having wireless and using windows for 3d/games. Now, of course, im screwed out of both.. thanks for the suggestion though- I really wish envy worked for feisty!

---

### Post by useResa on 2007-04-03
Sorry, I was under the impression that you were using Edgy.
There are also HOWTOs available for Feisty (however, you may have already visited those). For example [here](http://www.ubuntuforums.org/showthread.php?t=357501).

If indeed you are currently using Feisty, it may be worthwhile to post your question at the [Feisty Fawn Development](http://www.ubuntuforums.org/forumdisplay.php?f=179) forum. There are members there who know much more about Feisty and Nvidia than I do.

Sorry that I could not be of more help to you.

---

