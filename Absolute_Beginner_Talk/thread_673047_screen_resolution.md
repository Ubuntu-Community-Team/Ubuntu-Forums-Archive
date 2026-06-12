---
title: "screen resolution"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by markymry29 on 2008-01-20
when i ran ubuntu off the cd, i was able to get my normal resolution on my screen of 1440x900, but then after i installed ubuntu onto my computer, the settings won't let me run anything other then a screen setting of 640x480. i'm just wondering why that is. I have nvidia 6150 video card, and i even tried to run the restricted drivers for the card, and it still would not let me change the resolution to anything else but 640x480. any help would be greatly appreciated

---

### Post by Mud.Knee.Havoc on 2008-01-20
Anytime I've had this problem, manually modifying xorg.conf has fixed the problem.   You can find the proper section and add 1440x900 to each of the lines with the various resolutions listed.  Once you save this file and restart X, you'll be able to select it.

EDIT:  Please back up your xorg.conf file before doing this!!  And I am not the best at explaining this, so please take a half hour or so and read up on modifying your xorg.conf before jumping in.

---

### Post by Yoke &amp; Chung on 2008-01-20
If you have enabled the restricted driver, you can try changing the resolution by typing

sudo nvidia-settings 

at the terminal.

---

