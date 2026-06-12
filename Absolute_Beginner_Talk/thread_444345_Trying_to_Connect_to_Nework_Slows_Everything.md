---
title: "Trying to Connect to Nework Slows Everything"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by kajs on 2007-05-15
I installed Ubuntu on my Averatec 3200 laptop yesterday, and most everything seems to work fine, for at least what I'd like to use my computer for, except the internet. When I try to enable the wired or wireless internet connection, the computer slows to a crawl. After I turn it off, it works fine. But even when i do enable it, I still don't get the internet working. What could be the possible causes of this?

Thanks!

---

### Post by markmaus on 2007-05-18
Hello, I have an Averatec 3225 laptop.  I have the same problem.  I think that the video driver ¨via¨ for the S3 Unichrome video card is confusing the IRQs and causing my network cards not to work.  (Both wired and wireless).  I was able to get everything working by changing the video driver from ¨via¨ to ¨vesa¨ in the /etc/X11/xorg.conf file.  I don´t know how skilled you are at editing config files, so I won´t elaborate here.  If you don´t know how to do that let me know and I¨ll help you out.

---

