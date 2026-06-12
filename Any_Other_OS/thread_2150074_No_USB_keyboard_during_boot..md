---
title: "No USB keyboard during boot."
date: 2013-05-30
forum: Any Other OS
---

### Post by codingman on 2013-05-30
This morning, as I sat at my computer, I turned it on to be booted into the Slackware CD, where I boot my hard drive from. This is due to the fact that LILO has an issue and I never got to fixing it. Normally, I use the code:
```
huge.s root=/dev/sda2 rdinit=ro
```
... to get to Slackware on my hard drive. But today, as I used the command, it did not go through to the smaller font that meant that it was loading from my hard drive, instead, it seemed to be being processed on the disc entirely, and I had no usage of my keyboard after I typed in the command. Once it got to a certain line where it detected usb devices, it found the keyboard. After it found the keyboard, I could press num lock and such, but any key I pressed, it didn't change anything. When I disconnected the keyboard, it would respond that I had removed usb device *NUMBER*. And when I plugged it back in, it would show the manufacturer of the keyboard. Basically, the only thing I could do was to turn off the computer and reset.

---

### Post by mips on 2013-05-31
Check if legacy usb support is enabled in BIOS.

---

