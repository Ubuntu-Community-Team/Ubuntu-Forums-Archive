---
title: "Graphics driver broken"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by chajuram on 2008-04-05
Hi All,

I need help!!!

I was trying to install the ATI drivers for my ATI graphics card (Radeon HD 2400Pro) following the link 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0)

It does not work and at the end I get wrong rendering on my monitor. Pictures get highlights. 

In particular, I don't have the file "/etc/X11/xorg.conf", thats odd to me. Also, the step > sudo aticonfig --initial gives me the result
> Warning: Could not find configuration file
Please copy configuration file template to /etc/X11

Here is my system 
> Linux_____ 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux


I will be extremely grateful for any help and direction. 

Thanks,

Ritwik

---

### Post by skymera on 2008-04-05
This is a gift of god

```
 http://www.albertomilone.com/nvidia_scripts1.html 
```

I know ATI drivers are buggy, use Envy to install them.

---

### Post by chajuram on 2008-04-05
Thanks for your reply. 

In my efforts with this driver, I have also tried this, it didn't work then. I will give it another shot.

Ritwik

---

### Post by chajuram on 2008-04-05
Envy did not help me. :(

---

### Post by chajuram on 2008-04-06
Well, after many trials and errors, I removed the xorg.conf file and now I get back what Ubuntu had started with after the install. It is not using the ATI driver. I still can't change the resolution. 

Any help will be appreciated. 

Thanks,

Ritwik

---

