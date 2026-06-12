---
title: "Single boot on new hard drive"
date: 2008-11-16
forum: Apple Hardware Users
---

### Post by refader on 2008-11-16
A few weeks ago my macbook froze up while I was taking notes in class. When I restarted it, it wouldn't boot and only gave me the flashing folder icon. I used diskwarrior to try to repair any errors but diskwarrior could not see any hard drive so I figured it was shot. So I got a new 500 gig hard drive from ebay and then I downloaded and burned ubunto 8.10 on another computer and went through a guided install on my macbook. It seemed to complete normally but when I restarted it it will only give me a flashing folder icon still. When I put the ubuntu cd back in it automatically boots to that CD. I just want to be able to use ubuntu from my hard drive. Any help greatly appreciated!

---

### Post by hyperboloid on 2008-11-16
You might be a victim of the dreaded installer bug, as documented in this thread: [http://ubuntuforums.org/showthread.php?t=767677]("http://ubuntuforums.org/showthread.php?t=767677"). 

There are instructions in that thread that worked for me. (I'm also a single booter.) You probably will need to download rEFIt and burn a CD (on your other computer) and then boot into rEFIt using the CD. This allows you to fix your MBR. It's actually quite easy to do. 

Hope it helps.

---

