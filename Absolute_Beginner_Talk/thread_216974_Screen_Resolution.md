---
title: "Screen Resolution"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by ilkerka on 2006-07-16
Hi 
i have 17" samsung monitor and ATI 9600XT video card. I ve installed the drivers as stated on help. But my screen resolution is maxed at 1024x768. I remember making it 1150x... at the driver installation. How can i fix this problem?

---

### Post by Albi on 2006-07-16
Did fglrxinfo show a proper output?

---

### Post by ilkerka on 2006-07-16
ye no problem:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.5814 (8.25.18)

---

### Post by taurus on 2006-07-16
What is the max resolution for your monitor?  If it can't go any higher than 1024x768, it doesn't matter what you put in your /etc/X11/xorg.conf, it will not use it...

---

### Post by ilkerka on 2006-07-16
it can go up to 1240x... and also im using 1154x... on windows working fine

---

### Post by ilkerka on 2006-07-16
im on windows at the moment and my maximum screen resolution is 
2048x1536 so how do i configure my xorg.conf file to make the resolution 1152x864??

---

### Post by tuxcantfly on 2006-07-16
sudo dpkg-reconfigure xserver-xorg

---

### Post by Qwerty_ on 2006-07-16
I having some screen resoultion problems as well the monitor works fine at 1024X768 but when i plug it into my KVM the resolution drops down to 640X480 and when i go to change it i am not given any other screen resolutions other than the 640X480. I tried to edit the /tec/X11/org.conf and change the monitor to Generic Monitor but that lead me know where and i had to reformat my ubuntu. Any ideas why this would be?

---

### Post by ilkerka on 2006-07-17
i went through the steps again same result. It was asking about enabling kernel buffer i said no. Can this be the problem?

---

