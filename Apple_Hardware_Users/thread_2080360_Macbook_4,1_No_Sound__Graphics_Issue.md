---
title: "Macbook 4,1 No Sound / Graphics Issue"
date: 2012-11-03
forum: Apple Hardware Users
---

### Post by TrendyGuy on 2012-11-03
Hello all,

Brand new Ubuntu user and trying to learn. Just installed 12.10 and the biggest problem is I do not seem to be getting any sound. The drivers seemed to be installed and the system sees the hardware but nothing is coming out. I honestly do not know where to even start.

Second, I am getting to errors about my graphics hardware and saw that there is no driver installed for my graphics. Where do I go about getting that from and installing?

Greatly appreciate any help.

---

### Post by TrendyGuy on 2012-11-03
Sound works great when the headphones are plugged in but I get nothing out of the macbooks speakers when they are unplugged.

---

### Post by dirtyglove on 2012-11-08
i have the same macbook..had to downgrade to 10.10 cuz i cant figure my wireless.. u get that working??

---

### Post by Shutter4U on 2012-11-08
> **dirtyglove said:**
> i have the same macbook..had to downgrade to 10.10 cuz i cant figure my wireless.. u get that working??

I don't think you had to downgrade quite so far as 10.10. I am dual booting OSX Lion with 12.04 on my MacBook 4,1 and I am not having problems with sound or with wifi.

I answered your Ask Ubuntu question as well just a few minutes ago to tell you of my experience installing 12.04 with proprietary drivers selected. There's a "Broadcom" driver that, for me, was installed from the start and wifi just worked right away.

@TrendGuy: The headphone thing, I know there's a thread on the forums about that. Basically there's a switch of some sort inside the headphone jack. When you unplug the headphones or plug them in, the OS or the driver or something should recognize that the switch was pressed or released and respond accordingly. OSX drivers must be more sensitive to the device or something. Anyway, one workaround that people have been using when the headphones are unplugged but you're still not getting sound is to take a paper clip or pin or something that thin and insert it into the headphone jack and move it around until you activate the switch. Have some music playing or something so when it works you'll know because you'll hear it.

---

### Post by Popenuj on 2012-11-09
On my Macbook 2,1you just have to open terminal and type
```
alsamixer
```once the screen is up use the arrows to select <speaker 1> and press 'm,' this should unmute the headphone jack. Let me know if it's the same for a 4,1.

---

### Post by dirtyglove on 2012-11-09
> **Shutter4U said:**
> I don't think you had to downgrade quite so far as 10.10. I am dual booting OSX Lion with 12.04 on my MacBook 4,1 and I am not having problems with sound or with wifi.

I answered your Ask Ubuntu question as well just a few minutes ago to tell you of my experience installing 12.04 with proprietary drivers selected. There's a "Broadcom" driver that, for me, was installed from the start and wifi just worked right away.

@TrendGuy: The headphone thing, I know there's a thread on the forums about that. Basically there's a switch of some sort inside the headphone jack. When you unplug the headphones or plug them in, the OS or the driver or something should recognize that the switch was pressed or released and respond accordingly. OSX drivers must be more sensitive to the device or something. Anyway, one workaround that people have been using when the headphones are unplugged but you're still not getting sound is to take a paper clip or pin or something that thin and insert it into the headphone jack and move it around until you activate the switch. Have some music playing or something so when it works you'll know because you'll hear it.


i figured the broadcom, my mac just remembered them each time i upgraded in the software center..im currrently at 12.04 lts..wifi works but i want to use freaking skype w/ working video... thinking of going back down to 10.10 to do the isight tutorial to get the video working again?

[http://www.youtube.com/watch?v=m97YJ-Qfdi8](http://www.youtube.com/watch?v=m97YJ-Qfdi8)

[https://help.ubuntu.com/community/MacBook4-1/Maverick](https://help.ubuntu.com/community/MacBook4-1/Maverick)



whats the latest version of ubuntu i can have that has working video camera/manuel install? i just want my freaking skype lol

---

### Post by Popenuj on 2012-11-09
@dirtyglove I don't personally use my iSight but I am working on a way to fix this for you.

---

### Post by Popenuj on 2012-11-09
Sorry, I didn't really explore the links that you posted until now. Did you try this fix?

---

### Post by dirtyglove on 2012-11-10
> **Popenuj said:**
> Sorry, I didn't really explore the links that you posted until now. Did you try this fix?

yes i did, it took awile to do for some reason i was messing up mounting/locating the first part..but got it to work

---

### Post by piperbarb on 2012-11-11
I have the same MacBook.  I am dual booting OS X Lion and Ubuntu 12.04.  I do not have the sound issues.  Sound works perfectly using either laptop speakers, headphones or external speakers.  To get the webcam (iSight) to work, go to the link below and follow the directions.  It's really quite simple.
[https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight?action=show&redirect=AppleiSight](https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight?action=show&redirect=AppleiSight)

Be sure to read the directions first and follow the instructions.  It seems like a lot but it works very well.  I had to do that when I installed 11.10 and later 12.04.  Also, you can download Cheese from the Ubuntu Software Center.

Once you reboot, it should work.

---

