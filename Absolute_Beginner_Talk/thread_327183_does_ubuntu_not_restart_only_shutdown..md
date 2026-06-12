---
title: "does ubuntu not restart? only shutdown."
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by oilchangeguy on 2006-12-28
hi, i've tried 2 versions of ubuntu 6.06 (1 from ubuntu, and 1 from the book ubuntu unleashed), both work great, except they will not restart, only shutdown. is this something that's unique to ubuntu, not being able to perform a restart? please advise. thanks!

---

### Post by bruenig on 2006-12-28
There should be a restart option when you go to system>quit. If there isn't sometimes you can fix that by going to system>administration>login window and making sure the "show actions menu" option is checked.

If all of that fails, you can do this in the terminal
```
sudo shutdown -r now
```

---

### Post by oilchangeguy on 2006-12-28
i've not tried the command prompt to restart, but everything else is where it's supposed to be. both installs would not restart during the setup process. you can click restart all the processes shutdown then the computer just sits there and i have to use the power button to shut it down. does ubuntu take a while to restart? because in windows the restart process happens quickly.

---

### Post by Sef on 2006-12-28
You need to reset your power management settings in the BIOS.   When I had the problem, I changed mine from ON to AUTO and that got my reboot working.

---

### Post by oilchangeguy on 2006-12-28
i'll have to check the bios, i'm using a 5 year old toshiba laptop (upgraded along the way, 512mg ram, 40gb hd) with the old single screen bios, no multi choice tabs. but i'll look for any power options.

---

