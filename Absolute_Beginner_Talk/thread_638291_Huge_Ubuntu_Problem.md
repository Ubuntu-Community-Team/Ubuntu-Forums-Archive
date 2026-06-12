---
title: "Huge Ubuntu Problem"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Thosbob on 2007-12-11
Alright, heres whats happened: Ive been using Ubuntu for the past 6 months and just today my sound in all my applications dropped out. Rhythmbox gave a weird error that the resource wasn't available or that it was in use elsewhere. The Sound Preferences also was acting up giving a very odd string of errorcodes. So I do a little google-fu and found some stuff that suggested reinstalling the alsa drivers. I did this with the terminal ("sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils" followed by "sudo apt-get install linux-sound-base alsa-base alsa-utils") and everything looked fine so I rebooted hoping everything would work out. It didnt. My system now refuses to show a login prompt and when I boot it, hanging at a black screen. If I hit spacebar I get a command line which says "Valaria login: ". When I try to enter my username and password it freezes again and doesnt do anything. Now booting to recovery mode works just fine I get a prompt and alls well. I want to know if there is some way for me to either fix this problem or save the important files off of my hdd. Much thanks in advance.

---

### Post by Lvcoyote on 2007-12-11
It almost sounds like a hardware problem.  First thing I would do is download and run memtest86 to check your memory.  If that checks out then get a hard drive diagnostic too that you can use to check the hard drive for problems, most hard drive manufacturers have such tools available for download on their websites.

---

### Post by Thosbob on 2007-12-11
Ok fixed the non booting problem, I had killed gdm and ubuntu-desktop. Luckly a quick trip to the recovery console fixed that nicely and my GUI is back up and acting fine. Now the problem is that the sound still doesnt work. It recognizes my onboard sound and will try to play the test tone in the Sound thing (gave really wierd error before) but its not coming out the headphones. Files now also will appear to play in rhythmbox but no sound from the headies again. Any ideas, all the stuff Im using is the same as I have been for the past 3 months without issue.

---

