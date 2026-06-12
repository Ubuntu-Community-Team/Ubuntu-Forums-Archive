---
title: "iSight Jaunty problems"
date: 2009-08-29
forum: Apple Hardware Users
---

### Post by gotenks05 on 2009-08-29
Well, after having to restart my computer a bunch of times under Ubuntu Hardy, I decided to upgrade straight to Jaunty, by a clean install.  I liked how much easier it was to get the Internet and I got things set up the way I want, for the most part.  However, I'm encountering a problem.  My Mac's iSight is not working properly.  Yes, I install the isight firmware tools and did all of that stuff.  The problem is that when I open cheese up, everything is green, even the picture resulting from actually taking a photo is very green.  In Hardy, everything was as clear as Photo Booth on Mac OS X.  How do I fix this problem?

---

### Post by Rog-Mahal on 2009-08-30
The Jaunty libv4l is flawed. (Luckily, I've heard they already fixed it for the next release). The most reliable way that I've found to fix this is downgrade the libv4l to the one from hardy. Try the instructions [here.]("http://https://help.ubuntu.com/community/MacBook2-1/Jaunty#Reverting%20the%20Webcam%20Driver") Hopefully that will fix things, I know it did for me.

---

### Post by gotenks05 on 2009-08-30
> **Rog-Mahal said:**
> The Jaunty libv4l is flawed. (Luckily, I've heard they already fixed it for the next release). The most reliable way that I've found to fix this is downgrade the libv4l to the one from hardy. Try the instructions [here.]("http://https://help.ubuntu.com/community/MacBook2-1/Jaunty#Reverting%20the%20Webcam%20Driver") Hopefully that will fix things, I know it did for me.

Thanks for the help.  It works perfectly now.  Oh and your link did not go through very well, so I had to type of the address manually, using the link for guidance, but I did find the page you referred me to.  Now, I need to make a new liveDVD, so I will not need to deal with this issue again, if I need to reinstall Jaunty.

---

### Post by Rog-Mahal on 2009-08-30
Sorry about that, I tried get the page to jump right to the iSight section. Glad the fix worked! For any others wondering about the link, just look at [https://help.ubuntu.com/community/MacBook2-1/Jaunty](https://help.ubuntu.com/community/MacBook2-1/Jaunty)

---

