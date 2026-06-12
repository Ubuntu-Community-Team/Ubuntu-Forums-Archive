---
title: "Installed ubunto 7.04 on notebook with ATI x700, how do I fix resolution?"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Ramificatio on 2007-05-04
I just installed ubunto 7.04 on a notebook with an ATI x700 GPU and I can't select my native resolution which is 1280x800. The highest it will go is 1024x768. I also wonder if the drivers for my GPU is installed by default or if I have to manually install the drivers from ATI, which I tried. But it gives me an error that it must use X-ORG 7.1 or less and ubunto 7.04 has 7.2, so it will not install. Is there anyway I can solve this? I have searched for and tried different solutions to this but nothing works. Is there any other Linux distributions that would work better for my hardware, or is there a way to get it to work with ubunto 7.04?

Thanks.

---

### Post by luckyd on 2007-05-04
Have you tried installing drivers with the new restricted drivers manager? If not, it is under System/Administration/Restricted Drivers Manager
If that dosn't work try to reconfigure x-org to accept you resolution.
```
sudo dpkg-reconfigure xserver-xorg
```

---

