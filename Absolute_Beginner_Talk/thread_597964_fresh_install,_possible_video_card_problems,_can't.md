---
title: "fresh install, possible video card problems, can't boot up"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by onearmedpanda on 2007-10-30
i just reinstalled ubuntu after being left with no other option after buying a new video card and not being able to boot up. when i installed the new card the ubuntu loading bar would go about 1/10 of the way then stop. then which i switched back to my old integrated controller it worked fine. now i have a fresh installation of ubuntu and i have the same problem. please give me any advice you have, thanks in advance

---

### Post by overdrank on 2007-10-30
> **onearmedpanda said:**
> i just reinstalled ubuntu after being left with no other option after buying a new video card and not being able to boot up. when i installed the new card the ubuntu loading bar would go about 1/10 of the way then stop. then which i switched back to my old integrated controller it worked fine. now i have a fresh installation of ubuntu and i have the same problem. please give me any advice you have, thanks in advance

Hi when you reach the blank screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line hopefully.  Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

### Post by onearmedpanda on 2007-10-30
i can't open the terminal because ubuntu won't load

---

### Post by overdrank on 2007-10-30
> **onearmedpanda said:**
> i can't open the terminal because ubuntu won't load

Ok can you boot into recovery mode?
Then use the commands.

---

### Post by Maestro23 on 2007-10-30
> **onearmedpanda said:**
> i can't open the terminal because ubuntu won't load

Can you boot into Recovery mode?  If you can, it should take you to a command prompt.  Enter the commands posted above.

---

