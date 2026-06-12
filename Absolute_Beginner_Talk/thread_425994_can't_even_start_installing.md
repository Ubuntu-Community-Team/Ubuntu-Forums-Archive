---
title: "can't even start installing"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by mattigus on 2007-04-28
I'm real new to Ubuntu, and have never used Linux, and I figured I would try it out.

I have a burned CD with the latest Ubuntu on it.  I boot from it and select "start or install Ubuntu."  I see the loading screen finish, then my screen goes black, and stays that way.  I hear a start up sound that's music.  I think my problem is that it started up, but the video isn't showing.

Does anybody know how to fix this?  I have an AMD AMS dual core 4200+ with 2 gigs of ram and a Radeon x1800 graphics card.  I know theres a bug involved with the x series, but I can't even begin installing!

---

### Post by alienexplorers on 2007-04-28
Did you check the iso checksum?  What speed did you burn the CD at?

---

### Post by mattigus on 2007-04-28
I burned it at some extremely fast speed, like x144.  Should I have burned it slower?

What is checksum?

---

### Post by kvonb on 2007-04-28
Try starting up with the "safe graphics mode"

---

### Post by mattigus on 2007-04-28
the same thing happens to me in safe graphics mode.  From what I can tell, the video card is not outputting any video signal at all.  It's not even outputting a black screen.

---

### Post by mattigus on 2007-04-28
bump, if anybody else can help.

---

### Post by Seisen on 2007-04-28
You might need to burn at the lowest speed possible, anytime you burn the cd at high speeds  it can cause problems.

---

### Post by kvonb on 2007-04-28
Do you have an onboard video card, as well as the ATI?  Maybe it is defaulting to the onboard one.

Have a look on the back of the computer, is there another VGA connector?

Maybe try plugging your monitor plug into that to see if you get a signal.

If you do, then you will have to go into the computers BIOS and disable the onboard video.

---

### Post by mgmiller on 2007-04-28
You could try adding a parameter at boot time, before the screen goes black.  You should see some options on the bottom of the screen, Hit the one that lets you enter vga options and give it the command vga=792.  This forces it to use a specific resolution and color depth, in this case, 1024x768 at 24 bit color during the boot process.

---

### Post by sailor2001 on 2007-04-28
a rule of thumb is to burn iso image at 4x............what is your amd arch? 32 or 64?  Download proper one.

---

