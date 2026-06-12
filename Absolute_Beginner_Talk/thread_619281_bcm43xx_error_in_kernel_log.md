---
title: "bcm43xx error in kernel log"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Guruprasad on 2007-11-21
I am getting lot of errors  ¨bcm43xx_microcode5.fw not available or load fail¨ in kernel log.

computer also working slow.

how to rectify it?

---

### Post by wishyjr on 2007-11-21
im getting this too -is it something related to the wireless setup i have?

---

### Post by COLiNx86 on 2007-11-21
Try [this]("http://ubuntuforums.org/showthread.php?t=405990") That's what I did on 7.04 and .10 and it worked.

---

### Post by MaximusTG on 2007-11-21
The error relates to the firmware used by the opensource bcm43xx driver, the driver itself is opensource, the firmware isn't however. So on a default Gutsy install the bcm43xx driver is loaded, but then complains about the firmware not being installed. You can install the firmware through the restricted drivers manager.

---

