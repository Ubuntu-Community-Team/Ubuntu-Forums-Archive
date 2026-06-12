---
title: "Problem with my radeo X800 and Ubuntu 7.10"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by blakcode on 2007-12-11
Hi, I think I may have caused this problem so I am sure it's fixable, I just don't know how.

I have been installing and uninstalling linux distros and I finally decided to go back to ubuntu.

Now I had installed it earlier in the day and when I booted the live cd the resolution was too high I think, small bars at the top of windows. 

I ran the installer, got it all successful and was ready to start using. When I logged into my fresh 7.10 install it looked exactly like the live CD, small action bars and a thin black line on the left hand side of my monitor.

I ran the restricted drivers manager and activated my card. Rebooted and everything looked great, my card was working and my resolution 1360x768 was correct. 

Anyway, like I said this was my first install and everything worked the way I expected it too.

Later on while doing my second installed I was messing around with the live CD and decided to see what would happen if I tried to run the restriced drivers manager on the live CD. I did this. It told me I had to restart, but me being lazy was like "meh, I'll just install ubuntu already". When installed I logged into my new install and everything looked different than last time, this time instead of a thin black line on the left of my monitor I now have a massive fat black one on the right had side of it. The menu bars were also really fat now (well they are about normal size but they were much thicker than my first install attempt. 

First thing I decided to do was fix this and install my ati drivers from the restricted driver buddy.  After I had done this it told me to restart so I did and when I tried to boot Ubuntu I kept on getting a flicker message in the center of my screen saying: "out of range".

I then realised ah **** this must be because I was messing around with it on the live CD, so I decided to pop it back in and reinstall the way I did originally. When I booted up the live CD I was annoyed to find that it had the fat windows and the right hand black line just like my full install (where did the slim one go?!) 

As you can probably imagine I tried reinstalling ubuntu again but I am still getting the fat bar version. 


So now I need help getting it back the way it was. What has really stumped me though is why the live CD has suddenly god this new look. It's a cdr so files can't have changed.
No matter what I do though I can't get it to look the way it used to.

Anyone out there know what might be my problem?

Thanks.

---

### Post by spiderbatdad on 2007-12-11
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

