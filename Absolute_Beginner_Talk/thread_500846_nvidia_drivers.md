---
title: "nvidia drivers"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by phrozenb on 2007-07-14
Hello,

I had a stable version of Ubuntu running on my PC, i think it was 6.10 or something.

I'm a total noob to this. Then I saw there was a new version and from within X i click upgrade. It downloaded 600MB+ and installed on itself whatever it installed.

Then rebooted into the new kernel and X won't start. It says that "no screens found".

So far so good, I downloaded the latest version of drivers from [www.nvidia.com](www.nvidia.com) and installed them, allowed it to edit my xorg.conf file. Then hit startx, all good, almost everything working fine. 

Rebooted again, now it's back to "no screens found" ... Additionally it says that the version of the nvidia build is different from the version of the nvidia driver (but i just built it trough the nvidia install).

I don't want to install the driver each time.

Thank you for any answers.

---

### Post by kvonb on 2007-07-14
Download and install "envy" (I'm assuming you are now running Feisty 7.04, so get the Feisty version) from here:

[http://www.albertomilone.com](http://www.albertomilone.com)

If the standard automatic install doesn't work, try the manual option

---

### Post by phrozenb on 2007-07-14
I have no clue if I'm running Fiesty or not. I just hit the Update button and as I'm a noob I wouldn't know.

I know I'm running Ubuntu 7.04

However, envy seems to have fixed the problem: uninstall the old driver, install the new one.

Thanks

---

### Post by kvonb on 2007-07-15
Don't forget, every time an update to the kernel is installs, you will have to run envy again.

---

### Post by Ralob on 2007-07-15
I second the Envy way to install drivers. And 7.04 is indeed Feisty. 6.06 is what we call Edgy. 

I had this same problem, I fixed it by manually installing my driver through Envy. Don't worry, this is completely fixable.

---

