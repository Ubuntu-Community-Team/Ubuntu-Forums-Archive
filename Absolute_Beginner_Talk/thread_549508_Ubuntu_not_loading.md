---
title: "Ubuntu not loading"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by Spax579 on 2007-09-12
Hi, I recently installed the new version of Ubuntu 7.04 at the suggestion of a friend. I downloaded the alternate cd directly from ubuntu.com.
I tried installing it only to find that it would not read my cd drive; alright I thought...Whatever so I switched computers..Finally, after 2-3 days of trying different things, computers, software, video cards, ram..the works I got it to go to the install. I formatted the whole disk not wanting to partition my pc (didnt know if that would be useful later). So it tells me its going to reboot and I say, great finally..It gets to the loading screen and starts loading..it gets 5 bars from the end and freezes..I switch hard drives and try again on a different computer this time it finishes the loading process and then tells me server x failed..I'm somewhat patient but after this..I'm not sure what to do, if anyone could help I would be very greatful

The alternate computer got past the loading screen and then to server x failing, while my main computer only got to the loading screen.

Specs: 1 gig RAM, geforce 8800 gts, AMD athlon 3800+
Alternate: 2 gigs RAM, ATI x850 xt   Intel something(havent used it for a while)

Thanks
- Cody

---

### Post by skymera on 2007-09-12
since X dosent load, im guessign your Driver is incorrect.

when it dosent load type this in, i believe its correct. correct me if im wrong:

sudo dpkg-reconfigure xserver-xorg

then follow through. yada yada. and select your driver.

have a guess at Vesa :D

---

### Post by Spax579 on 2007-09-12
Unfortuanitely I have no idea where I'm supposed to type this, I am a complete linux noob. After it gives me the error for server x it gives me a text based login with no gui and whenever i type in the username and hit enter, it wont let me enter anything for the password. It does however offer to let me see a detailed explanation for the server x failure; I can put some of the code in this thread if it would help..Let me know

Thanks
- Cody

---

