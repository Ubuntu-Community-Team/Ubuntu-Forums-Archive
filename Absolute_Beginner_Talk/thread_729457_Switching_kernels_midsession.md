---
title: "Switching kernels midsession"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by Majiq on 2008-03-19
This is a completely random idea, but it's something that would make my life so much easier. I was wondering if there is a way to almost hot-swap kernels. 

I have two externals (an old AcomData 250GB (= SIDEKICK, for ease) that has an external power source and a new WD 160GB (= APPRENTICE) that runs off the USB) and I frequently need to use APPRENTICE as my data-carrier, because it doesn't need external power and I no longer have flash/thumb/insert-new-fangled-name-here drives. They both have Ubuntu Gutsy 7.10 installed on them with similar setups. I was wondering if there is a procedure or method or something that I could go through to switch kernels. For example, if I needed to use go from APPRENTICE to SIDEKICK because I needed to leave, I wouldn't need to shutdown my computer to unplug it - just execute code and grab and go. Or going in the other direction, when both of my externals are plugged in, SIDEKICK takes precedence (for some reason), and I prefer to stay on APPRENTICE, so I need to restart my computer to switch over. If I could do this without actually restarting my computer, it would be nice.

Both installs have the same setup insofar as kernel version, video drivers, users, and preferences. The only real difference is the number of programs (SIDEKICK only really has essentials for when I let others use/borrow APPRENTICE) and possibly some key setups.

Any suggestions?

---

### Post by bodhi.zazen on 2008-03-19
I do not think you can switch kernels without rebooting, but of course that may be possible.

I think what you are looking for is chroot.

something like this :

[http://www.pixelbeat.org/docs/chroot.html](http://www.pixelbeat.org/docs/chroot.html)

---

