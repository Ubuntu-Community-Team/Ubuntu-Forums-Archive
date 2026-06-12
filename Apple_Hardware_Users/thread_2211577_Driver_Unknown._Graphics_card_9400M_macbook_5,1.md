---
title: "Driver Unknown. Graphics card 9400M macbook 5,1"
date: 2014-03-16
forum: Apple Hardware Users
---

### Post by trakis on 2014-03-16
Hello,

Prior to this post I had researched several others in hope of an answer but without any luck. Maybe I did the searches wrong but I do not come up with anything else so I need some help with this issue.
Is the 'configuration', I guess, of my graphics card which does not show up when I go to system > details > overview. It shows:

Ubuntu 12.04 LTS

Graphics Unknown
OS type     64-bit

and then I go to > details > Graphics

    Driver Unknown
Experience Standard


so I write in terminal:

```
$ lspci | grep VGA

02:00.0 VGA compatible controller: NVIDIA Corporation C79 [GeForce 9400M] (rev b1)
```

and:

```
$ lspci -nnk

02:00.0 VGA compatible controller [0300]: NVIDIA Corporation C79 [GeForce 9400M] [10de:0863] (rev b1)
    Subsystem: Apple Inc. MacBook5,1 [106b:00aa]
    Kernel driver in use: nvidia
    Kernel modules: nvidia_331, nvidia_331_updates, nouveau, nvidiafb

```


Thank you in advance for any hint or clue that might help me.

---

