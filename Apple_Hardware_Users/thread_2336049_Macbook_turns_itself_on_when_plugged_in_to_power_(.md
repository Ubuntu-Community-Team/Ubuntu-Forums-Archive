---
title: "Macbook turns itself on when plugged in to power (as well as a PRAM question)"
date: 2016-09-04
forum: Apple Hardware Users
---

### Post by Roasted on 2016-09-04
Hi friends. I'm tinkering with a Macbook Pro that turns itself on when plugged into power. If the laptop is off, lid closed, and I plug it in to charge it just kicks on. I did some reading online and saw a number of people have spoken about this on Apple forums before. While nearly all of them didn't provide an actual solution and the threads seemed to fizzle, one user did say this:

```
if you go into system properties and then system saver. click on the schedule 
button towards the bottom right and see if you have it scheduled to wake at a 
certain time. if it misses this time when it is off ac power, the next time 
you plug it in it will turn on because it missed its scheduled turn on.
```

Sounds plausible. Only catch is, there is no Mac OS on this laptop -- just Ubuntu 16.04. Is there a way to change this? Or am I looking at tossing in a different drive to install OSX to simply check/switch this setting? If I have to do that, I can... I mean it's the penalty for using Apple hardware I suppose. Just tinkering around with it so it's not a big deal, but it had me curious enough to look further.

For what it's worth, I did notice in my very limited testing that if I have the laptop closed, powered off, plug in power, and simply let it go, it does ultimately go to sleep. I hear the quick drums when the system arrives at the login screen, though if I simply ignore it and let the laptop closed, it goes to suspend mode about 10-15 seconds later. So... if nothing else... that's good at least... but like I said, still curious enough to see what others have seen/are seeing + if there's a way around them.

P.S. - I cleared the PRAM on this as well in an effort to troubleshoot. Interestingly, once I cleared the PRAM, the system would no longer boot to Ubuntu. It would fire up, I'd hear the chime, and I'd be ultimately left with a black screen with a flashing cursor -- nothing else. I ended up booting to a live instance of 16.04 on a flash drive, ran boot repair (love that utility), and it was bootable again afterwards (it did say there was an error, though upon rebooting it brought me back up as I was hoping). Curious - has anybody else ran just Ubuntu (not a dual boot) on Apple hardware and cleared PRAM? If so, have you noticed this behavior? This had me wondering if anybody else had ever seen that particular scenario before. 

Thanks for any and all insight!

---

