---
title: "Ubuntu won't boot up anymore after uninstalling ALSA"
date: 2005-09-15
forum: Absolute Beginner Talk
---

### Post by mustang on 2005-09-15
Ok, so I was having problems with ALSA (don't ask) and I spent hours on end asking around for help and searching google to get the sound working. I tried many suggestions but I never got sound working with ALSA (works fine under OSS mind you)

So I figure, you know what, lets start from a clean slate and I go to Synaptic and search "alsa" and mark everything for complete removal. Uninstalling audio drivers shouldn't break anything right? Well apparently it did. When I rebooted, Ubuntu gets stuck at a blank screen with a small cursor blinking in the upper right hand corner. 

So I go into recovery mode (which works absolutely fine) and type in "sudo get-apt install alsa" which install alsa and alsa-base I think. So that went okay and I rebooted--no cigar--still get the same blank screen. So now I'm here...looking for some help.

Thanks guys

---

### Post by heimo on 2005-09-15
Maybe you accidentally removed something else too? (it's possible through package dependencies) I would try to install ubuntu-desktop and ubuntu-base packages to make sure you're not missing anything important.

 ```
sudo apt-get install ubuntu-base ubuntu-desktop
```

---

### Post by mustang on 2005-09-15
Thank you heimo! :) That worked perfectly. Do you think that because I selected "remove completely" versus just "remove" that it messed up other programs? What is exactly the difference between the two? 

Oh, and if I may ask, rather than creating another thread, when I go to applications->system tools->add/remove programs, it just hangs at the screen and nothing shows up. Does anyone know what the problem could be?

---

