---
title: "Half speedtouch"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by richardward101 on 2006-07-14
got my speedtouch working using  [https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch) but theres a problem. I'm with bulldog 8 meg, but I consistently get speeds of exactly half that! I'm wondering if there are any other drivers that would do the job better? Or am I going to have to splash out on a router?
Thanks...

---

### Post by coffeecat on 2006-07-14
There's two issues here, but first, well done for getting the Speedtouch working. I did the same last year for both Ubuntu and Fedora, but I count it as one of my less fulfilling Linux moments. :wink:

USB was never designed for networking and is slower than an ethernet connection, but I don't know whether this is the reason you're getting 4Mbs instead of 8Mbs. This apart, do consider getting yourself a proper ethernet modem/router. They're designed for the job, unlike those usb nasties. Far less hassle to set up and you get the security of a good built-in firewall and NAT.

But I think it far more likely that your speed issue is down to the nature of the new MAX 8Mbs service. The speed **will** vary from day to day, and 8Mbs is a theoretical maximum. You need to be next door to the exchange and no one else on line to get it. I upgraded from the 2Mbs service in April, and my download speed didn't go up until June. (There were troubles and bugs down to BT Wholesale in May.) Now my speed varies from about 3 to 6 - usually between 4 and 5, and I'm not complaining because many servers can't keep up anyway.

But not the Ubuntu servers. They almost always give good speed. But of course. :)

Edit: Forgot to say. Your ISP should have more to say on expected speeds with the 8Mbps MAX service. Check out their website.

---

### Post by richardward101 on 2006-07-15
Initially I assumed this was the case, we had hellish speeds on out ntl line for the same reason, but the thing is that its consistent, when I download lots of stuff, it ALWAYS downloads it at EXACTLY the same speed!
I would test it in windows for an affirmative answer, but windows wants nothing to do with it! It worked first time in ubuntu following the tute, but windows doesn't like it (admittedly its vmware, but still). The plan was eventually to use the ubuntu box as a router, as I want bandwidth shaping.

---

