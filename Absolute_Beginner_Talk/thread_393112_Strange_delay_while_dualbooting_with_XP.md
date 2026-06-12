---
title: "Strange delay while dualbooting with XP"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by brennydoogles on 2007-03-25
I have recently becaome a huge fan of Ubuntu, and decided to share its many blessings with my family. While setting up the dualboot for the third computer, I have discovered a strange and highly annoying phenomenon. Between selecting the OS and Ubuntu loading, there is a 3-4 minute pause where the screen is black, and nothing is happening. After Ubuntu loads everything runs at a decent speed, and while booting into Windows XP from the same process, there is no delay. I do want to mention, that this is the only dualboot I have set up using two hard drives, with ubuntu being on the slave drive. Is this normal, and is there a way to change it?? Thanks in advance for everyone's help.

---

### Post by benerivo on 2007-03-25
I'm not sure, but it sounds as if Ubuntu is going through some sort of drive check as it initially tries to mount the root (/) partition. I believe whether Ubuntu checks this or not is determined by the settings in the etc/fstab file. If you open this file and find the line for the root partition it will end with two digits. I can't remember off hand exactly what they stand for so do google for it or check the forums, but you could *risk* changing the last two digits to 0 0 which will force Ubuntu to skip this initial check when mounting root.

---

