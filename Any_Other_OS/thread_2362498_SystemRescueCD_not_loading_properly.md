---
title: "SystemRescueCD not loading properly"
date: 2017-05-29
forum: Any Other OS
---

### Post by cigtoxdoc on 2017-05-29
I downloaded the ISO image and burned it to a CD-ROM using xfburn.  On PC that needs help, the gave numerous I/O errors and finally got to login, and apparently you are supposed to enter "none".  Then program stops and only way to recover is reboot button.  Next tried it on perfectly working PC.  Same thing happens.  Forum for SystemRescueCD is not taking new members.

Can someone provide instructions on how to make program work.

Thank you,

John

---

### Post by Bucky Ball on 2017-05-29
When it 'stops', what are you getting? A cursor in a CLI? If so, type 'startx' and see what happens.

---

### Post by yancek on 2017-05-29
SystemRescueCD does not boot to a GUI.  On boot, it will stop at  language selection where you need to enter one of the codes shown for your language.  Failing to do that, it will default to English.  After that, you should see a message about running net-setuo eth0 if you want to configure your wired connection and below that, it states explicitly to type:  startx and hit enter to get to a GUI.

---

### Post by Bucky Ball on 2017-05-29
Thank you for filling in a fuller explanation, yancek. :)

I love that thing, but haven't needed to use in awhile.

---

### Post by howefield on 2017-05-30
Moved to the "*Any Other OS*" forum.

---

