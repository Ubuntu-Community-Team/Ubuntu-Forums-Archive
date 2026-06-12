---
title: "screen saver prob"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by silent1643 on 2007-05-11
upgraded to ubuntu studio from ff and now if i preview a screensaver or wait until it loads it logs me out and then i have to reload??? i have an ati radieon 850x card..

---

### Post by Valinski on 2007-05-11
I had a problem like that with my NVIDIA driver. 

Does the screen go black then wait a few secs before asking you to log in?

I had to enable the restricted drivers database to solve it... The thing was for me X server wouldnt start then cos i hadn't set it all up properly. 

Envy sorted it out tho! 

Dont know if thats much help but its sounds similar to a problem i had for a while!

---

### Post by silent1643 on 2007-05-11
> **Valinski said:**
> I had a problem like that with my NVIDIA driver. 

Does the screen go black then wait a few secs before asking you to log in?

I had to enable the restricted drivers database to solve it... The thing was for me X server wouldnt start then cos i hadn't set it all up properly. 

Envy sorted it out tho! 

Dont know if thats much help but its sounds similar to a problem i had for a while!

yeah it does go black for a few then logs out.. i tried envy before and my title bar on every application disapeared. so i had to uninstall the drivers it installed for my ati

---

### Post by Valinski on 2007-05-11
How long ago did you try it? cos i tried it about just after the update to FF and it didn't work.....Then i tried it a day later and it had been updated! 
 

Does it do the same if you try and run a program that uses 3D?

It did the same with my emulators. 

Its hard for me to suggest anything more conclusive since i was also battling for months with the issue. I just had a bit of luck in the end with envy and the god send that created it!

---

### Post by silent1643 on 2007-05-11
> **Valinski said:**
> How long ago did you try it? cos i tried it about just after the update to FF and it didn't work.....Then i tried it a day later and it had been updated! 
 

Does it do the same if you try and run a program that uses 3D?

It did the same with my emulators. 

Its hard for me to suggest anything more conclusive since i was also battling for months with the issue. I just had a bit of luck in the end with envy and the god send that created it!

maybe 3 or 4 days ago i tried envy, i dont think they are updating it anymore? could be wrong.. i haven't really tried anything else cd, i can open blender fine and of course i can't run any type of desktop effects because of my ati card, so i guess im screwed until ubuntu fixes the ati and nivda issues :D

---

### Post by Valinski on 2007-05-11
Yeah but i'm not sure how much they can do with it being a restricted driver. But what do i know! :) 

One thing i did notice when I was having troubles is that my XORG.conf file in the NVIDIA menu was quite different do the one that people tell you to edit through terminal. 

I dont know if that means anything as im not too clued up and just learning myself but it could have something to do with why so many peoples X server wont start if its got conflicting information! 

Again im just stabbing in the dark.

---

