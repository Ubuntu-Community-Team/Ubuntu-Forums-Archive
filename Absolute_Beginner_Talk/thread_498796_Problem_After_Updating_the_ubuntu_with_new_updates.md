---
title: "Problem After Updating the ubuntu with new updates"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Sivabalan Balasundram on 2007-07-11
Hi, 

    I have already manage to install the ubuntu 7.04. My first login to ubuntu was fine. After i have configured my internet settings, i tried updating my ubuntu with the available updates. How ever, the update was slow and i decided to cancel the update in the middle of the update proces. The system hanged and i had no other option other than force quit the OS by turning OFF the power. I tried to login to ubuntu OS again but i have a blank screen with the hour glass. Can someone help me with this?? 

Thanks.

Regards,
Sivabalan Balasundram

---

### Post by Inxsible on 2007-07-11
Log in to the recovery mode and type in this command

```
sudo aptitude update
``` then wait for the updates to complete !!

Then do ```
shutdown now
``` then try logging into your Ubuntu.

See if that works

---

