---
title: "RAM test fail"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by abhilash82 on 2007-08-23
Hello,
I have a P4(2.40 GHz) with Intel motherboard (865GBF), 128MB x 2 DDR RAM and running on a dual boot with Windows XP and Linux. My Linux (Xubuntu) which requires 256MB to run starts cleanly but over a period of time (maybe after 1 hr of use) it starts to become unresponsive. I dont have any significant problems like this in my Windows XP but is still on the slower side. I did a RAM test using Windows Diagnostic Memory test and Memtest86 softwares. Both tests resulted in only one test condition being passed out of 6 . I have subsequently tried to remove and clean the gold plated contacts of the memory and have also changed and swapped the slots but still I get the same test errors. I would like to know how my OS ( both XP and Linux) work even with so many bad address locations in the RAM? Is it to do with a faulty motherboard or RAM? The other thing I noticed is that my swap memory usage in xubuntu is very less initially and reached maximum in a hours time.I would like to find this out before I take a step to replace my current RAM(probably with 1GB).
Thanks
Abhilash:KS

---

### Post by Jimmyfj on 2007-08-23
Have you tried booting up on your Xubuntu Cd and run the memtest from that? Does it report the same errors as in Windows?

---

### Post by abhilash82 on 2007-08-23
Yes, I have run the memtest option in the Ubuntu Live CD also and it gives RAM address location errors. But what would be the reason behind my swap space getting exhausted so soon??

---

### Post by mcduck on 2007-08-23
> **abhilash82 said:**
> Yes, I have run the memtest option in the Ubuntu Live CD also and it gives RAM address location errors. But what would be the reason behind my swap space getting exhausted so soon??

If you use Firefox or any other memory hog application it easily eats the ram you have pretty quickly. And after that swapping starts..

Anyway, if Memtest shows any errors one of your RAM sticks is broken, that's absolutely sure. You should replace it as soon as possible, as broken RAM _will_ cause problems, and in worst cases even corrupt your files and operating system.

If you want to test which stick is the broken one don't swap the sticks to different slots, instead remove one completely and run Memtest again. Then try the same with the other stick.

Anyway, you would really benefit from having a bit more memory than what you have now. With a 2,4GHz P4 having only 256MB of RAM sure is the biggest bottleneck slowing your system down. So while you are replacing the memory you should upgrade to at least 512MB. Besides, at least in here, one 512MB stick costs actually less than 128MB sticks..

---

