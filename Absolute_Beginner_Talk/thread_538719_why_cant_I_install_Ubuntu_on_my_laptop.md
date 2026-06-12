---
title: "why cant I install Ubuntu on my laptop?"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by fosix on 2007-08-30
Hi guys, my laptop is ASUS M2N with Windows XP, I got Ubuntu 7.04 CD via mail.

After setting the priority of booting, I could enter the first sight of Ubuntu installation with 30 sec counting down, I pressed 'enter', then screen becomes black after quickly showing loading kernel with the cursur blinking all along even after 10 min. So what might be wrong? I am a beginner of Linux.

---

### Post by igknighted on 2007-08-30
> **fosix said:**
> Hi guys, my laptop is ASUS M2N with Windows XP, I got Ubuntu 7.04 CD via mail.

After setting the priority of booting, I could enter the first sight of Ubuntu installation with 30 sec counting down, I pressed 'enter', then screen becomes black after quickly showing loading kernel with the cursur blinking all along even after 10 min. So what might be wrong? I am a beginner of Linux.

When you get to the 30sec countdown, hit F6 and a line of text will show up towards the bottom of the screen.  Delete the words "quiet" and "splash" and then hit enter.  This will make the computer show more info during boot.  It will fail again, but there should be an error message visible.  Could you post that back?

---

### Post by Teamgeist on 2007-08-30
The solution is to put the option nolapic after the words quiet and splash.
So hit F6 and after "quiet splash" put nolapic.

I own a Asus M2N myself and that's how to fix this problem. The Laptop works with no restrictions afterwards.

Here is the bugreport on [www.launchpad.net](www.launchpad.net)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/83290](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/83290)

It would be very nice if you could confirm this bug there.

If you have any problems, just post back here.

---

### Post by fosix on 2007-08-31
> **Teamgeist said:**
> The solution is to put the option nolapic after the words quiet and splash.
So hit F6 and after "quiet splash" put nolapic.

I own a Asus M2N myself and that's how to fix this problem. The Laptop works with no restrictions afterwards.

Here is the bugreport on [www.launchpad.net](www.launchpad.net)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/83290](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/83290)

It would be very nice if you could confirm this bug there.

If you have any problems, just post back here.

thank you very much! I have reported this bug, and I will try again tonight.

Have a nice weekend!

---

