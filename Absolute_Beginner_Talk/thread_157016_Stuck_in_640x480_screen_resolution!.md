---
title: "Stuck in 640x480 screen resolution!"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by shyopstv on 2006-04-08
Hi I have been using Ubuntu for about a week with a resolution 1024x768 but I booted it up last night and everything looked really huge. After checking the screen resolution using the GUI, I noticed that I was in 640x480 and that was the only option available! I don't think it is a hardware fault because I can still run at higher resolutions in Windows - drivers maybe? Can anyone offer any other suggestions? I tried rebooting but I still can't change the res.

Thanks


EDIT: No need to worry. I just booted up again and it is in the normal resolution. Once again computer exhibit their mystical ability to magically repair themselves :-)

---

### Post by patrick295767 on 2006-04-08
did you try:

```
sudo dpkg-reconfigure xserver-xorg 
```

??

Greetings

---

### Post by shyopstv on 2006-04-08
Nope. I just rebooted and it was in the correct resolution but thanks for the code anyway

---

### Post by YuHoo on 2006-04-08
Yes, computers fix themsevles, I don't get it. If you continue to have problems with it you should double check your drivers. Do not always use the latest release, but the latest stable release if you have troubles. When this has been solved, you might want to reconfigure the X11.

```
sudo dpkg-reconfigure xserver-xorg
```

That should probably fix most of your problems, if not, post again or pray that your computer exhibits magical properties again (which it will:mrgreen:)



....... dang, slow again......

---

