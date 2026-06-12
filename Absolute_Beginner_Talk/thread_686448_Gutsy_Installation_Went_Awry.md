---
title: "Gutsy Installation Went Awry"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by robere.it on 2008-02-03
Alright. I'm relatively new to the Linux scene, and I've been working with Kubuntu 7.04 for a while now. Today I attempted the upgrade to gutsy through Adept, then halfway through it messed up. I used sudo dpkg --configure -a, and the rest of the packages appeared to go through. BUT, now whenever I open Adept, i get 

Could not find mime type 

application/octet-stream

And whenever I open Dolphin or Konqueror, I get 

Malformed URL
file:///home/robere

then

Could not find mime type
application/octet-stream

then

no mime types installed

and then finally, when dolphin/konqueror opens, there are no files present in any directory, or even directories for that matter (Home, system, etc. are still on the sidebar, however nothing appears in the main window). Now, when I use Konsole, I can still navigate files. 

Any suggestions? I'm really really afraid to restart.

---

### Post by jaytek13 on 2008-02-03
I don't have a solution (always nice to preface a post with that eh) but I can say this same thing happened to me the other day with Kubuntu 7.04. After downloading all the packages adept froze at the first package it tried to install. After that, I did what you did and it resumed, got another error, did it again, everything seemed to go through. 

So, I restarted my computer and had the same problems that you are having no. There were no more upgrades to be had, but nothing was right. I searched for a while for a solution, but apparently not many people have encountered this problem.

Anyways I decided to just say screw it and reinstall 7.04 and try again. So I did, went through the upgrade process again, this time with no issues at all.

---

### Post by robere.it on 2008-02-03
No worries. After an afternoon of toying away with it, everything seems to be alright. I managed to get everything back to normal, which is probably more then a lot of people can say.

---

