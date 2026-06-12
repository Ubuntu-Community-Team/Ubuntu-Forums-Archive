---
title: "Robotics external modem model 5686"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by mamut0o1 on 2008-01-17
Hello I recently install Ubuntu on my pc, I have a robotics external modem; I have it hooked up using a 25pin male to a 9 female to com port. I'm really lost on how to make this work. I tried command wvdialconf and it doens't detech my device, i tried setting it up from Admin>network> set to ttyS0 and ttyS1 to see if I get lucky but no luck there eather... I did dmesg | grep ttyS* to check my ports and it makes a list of my com ports but the Modem is just not detected. Can any1 please help me.

mamut

---

### Post by dstew on 2008-01-17
From a command line, enter **sudo setserial**. This should list the active ports, if any. See the [setserial man page.]("http://linux.die.net/man/8/setserial")

---

