---
title: "[SOLVED] HELP! Can't get past splash screen."
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by rouge568 on 2007-10-13
I was using an up to date gutsy beta, with latest kernel, when I decided to reboot  (for alsa reasons). However, when I turned the computer back on, I got up to the splash screen, it finished, and then nothing. Oh sure, there was something, but that something was limited to a flashing white underscore on a black screen. I am getting no response from both keyboard and mouse. I tried rebooting several times to no avavil, and am now forced to use my Puppy cd to write this. Any help would be very appreciated.

---

### Post by Bliepo32 on 2007-10-13
It seems you have the same problem as I do. I have seen more users having this problem. Luckily, I do have a tamporary fix:

First, we make a back-up.
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

```

You can restore the back-up if needed with:
```

sudo cp /boot/grub/menu.lst.backup /boot/grub/menu.lst

```

The we will have to edit menu.lst. So we open it in nano (or wathever text neditor you want):
```

sudo nano /boot/grub/menu.lst

```

Then search for 'quiet' and 'splash', and remove them. Then save the file.

---

### Post by rouge568 on 2007-10-13
Thanks, but the problem seems to have resolved itself.
I loaded into recovery mode and tried to update (to see if it was a broken package), but it didn't seem to recognize the internet connection. oh well. So I rebooted and this time it worked. Still not sure why, but im just happy it does.

---

