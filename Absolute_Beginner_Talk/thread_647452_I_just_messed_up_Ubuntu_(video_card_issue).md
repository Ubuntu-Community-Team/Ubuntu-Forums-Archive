---
title: "I just messed up Ubuntu (video card issue)"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by flightrecorder on 2007-12-22
i had a perfectly working dual boot of xp and ubuntu until yesterday. ubuntu had recognized my Nvidia card as a restricted driver and display was working fine. for some reason, i changed my generic Nvidia driver to the specific model driver and everything went to hell from there. when i boot up my monitor gives me an out of range error message. how do i restore ubuntu? i know what the problem is, i just cant get into ubuntu. i also have no idea how to use recovery mode in the terminal.
thanks

---

### Post by jken146 on 2007-12-22
```
dpkg-reconfigure xserver-xorg
```  will allow you to set your X server up again.

---

### Post by flightrecorder on 2007-12-22
worked well, thanks.

---

