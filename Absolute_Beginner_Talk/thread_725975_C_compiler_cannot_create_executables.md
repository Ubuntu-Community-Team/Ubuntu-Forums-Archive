---
title: "C compiler cannot create executables"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by perito on 2008-03-16
```

ubuntu@ubuntu-laptop:~/alsa-driver-1.0.16$ ./configure --with-cards=hda-intel
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
ubuntu@ubuntu-laptop:~/alsa-driver-1.0.16$ 

```

what should i do to make it compile?
It worked on another pc with fiesty but now Im trying to do the same on gusty and its giving this error... please help

---

### Post by Ub1476 on 2008-03-16
Are you sure audio isn't working already? If it's an Intel, and your computer is about 1 year old, that's odd.. Make sure speaker and such isn't muted:

```
alsamixer
```

Did you follow the [HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto") (make sure required tools/dependencies is installed)?

---

### Post by taurus on 2008-03-16
You need the build-essential package.

```
sudo apt-get update
sudo apt-get install build-essential
```

---

