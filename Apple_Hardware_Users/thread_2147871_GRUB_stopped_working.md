---
title: "GRUB stopped working"
date: 2013-05-23
forum: Apple Hardware Users
---

### Post by swarup on 2013-05-23
I have a Macbook Pro set up with a dual boot into OSX and Ubuntu 9.04. The system is wonderful, and for five years I have never had even a hint of a problem. It is set up with rEFIt, so when you boot up it first goes to the rEFIt menu screen where you select OSX or Linux. If you select Linux (which I do 99% of the time), it then goes to the standard GRUB menu screen, where upon selecting Ubuntu (the only OS set up there), it boots up into Ubuntu. This morning out of the blue when I boot up and select Linux at the rEFIt screen, it acts as though a GRUB menu screen is about to appear. But instead of that, it just gives a black screen with the words "GRUB" appearing in the upper left hand corner of the screen. So I am guessing that perhaps GRUB became corrupted somehow. What do I have to do to get GRUB working again? (This is urgent-- I can't do any of my work until GRUB works, so I can get into Ubuntu.) Thank you!

---

### Post by swarup on 2013-05-23
Please don't be scared off from writing because this is an apple system-- once I click the "Linux Penguin" on my initial boot up menu (i.e. rEFIt menu screen), it goes directly to the GRUB screen and from there it is pure linux. So perhaps best is to just treat the problem as though GRUB has gotten corrupted. When GRUB is corrupted, what is a general user to do, in order to get GRUB working again?

---

### Post by Bucky Ball on 2013-05-23
I am stunned you are only now having problems as 9.04 reached end of life and has not been supported with updates, including security updates, for two and a half years. I don't know there's much point pursuing a fix for this as it could be anything. Also could be obvious to those familiar with refit.

My advice, although off topic from your issue, is upgrade to a supported release. You are running a security risk if this machine is online (which is why this could be anything).

(There is a Mac/Apple sub-forum you would be best posting in in future here: [http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328))

---

### Post by swarup on 2013-05-24
Just needed to reinstall GRUB. For anyone who may find themselves in a similar situation, [Here]("http://mac.linux.be/content/problems-refit-and-grub-after-installation") is a great link which tells you how to do it. Now my beloved 9.04 is back up and running, smoother than ever. I wouldn't trade it away for anything.

---

### Post by Bucky Ball on 2013-05-24
Glad to hear it's fixed but if you're online, you are running a security risk with 9.04. Your choice. I suggest you create a spare partition and start testing other releases/flavours because a change has gotta come eventually. If you don't like Unity then Xubuntu 12.04 LTS might be an option. ;)

To help others, please mark thread as solved by following the link in my thread. Thanks and good luck.

---

