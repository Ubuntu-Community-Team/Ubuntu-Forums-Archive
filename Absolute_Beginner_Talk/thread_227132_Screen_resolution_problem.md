---
title: "Screen resolution problem"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by Jiminew on 2006-08-01
I am running Ubuntu from the disk I downloaded the other day... however the resolution default is 800x600 (I think) so I can't see enough of the screen to install the thing! I have tried searching the forums etc and none of the fixes I have attempted have worked. I haven't used Linux before so don't know what I'm doing. I have a Voodoo 3dfx driver and L15c flat screen monitor. Please help!

---

### Post by Namingishard on 2006-08-01
Can you see the top panel? i think its under admin >> Screen resolution

---

### Post by Jiminew on 2006-08-01
Hi, thanks for replying. I tried that first of all, then I tried using the help on the website which involved copying and pasting commands into a terminal, nothing has worked. So now I'm downloading Mepis to see if that automatically detects my hardware. Fingers crossed. Cheers

---

### Post by buythe2ndglance on 2006-08-01
Did you try looking in the bios settings?  I had a problem where it looked like the resolution was set for a widescreen monitor.  I lost about an inch from the left and right sides of the monitor.  I had to go into the bios and look for select display device and change it to CRT instead of CRT/TV this fixed most of my screen resolution problems.  My posting was "monitor problems" and was posted on the 31st of july.

---

### Post by gils0040 on 2006-08-01
try sudo dpkg-reconfigure xserver-xorg. when you get to the screen that lets you select resolutions make sure that you check the higher resolutions that you want.

---

