---
title: "1920x1200 Resolution"
date: 2009-11-01
forum: Apple Hardware Users
---

### Post by FirstNameRyan on 2009-11-01
I've just installed Ubuntu 9.10 on my 24" iMac using Boot Camp. I'm interested in learning to use and understand Linux, but 1280x720 is just horrid to use on a 24" monitor. Is there anyway to add 1920x1200 as an option?

---

### Post by rifak on 2009-11-02
type this command in the terminal:

```
gtf 1920 1200 60
```

copy the output and paste it in here

---

### Post by brucem91 on 2009-11-02
> **FirstNameRyan said:**
> I've just installed Ubuntu 9.10 on my 24" iMac using Boot Camp. I'm interested in learning to use and understand Linux, but 1280x720 is just horrid to use on a 24" monitor. Is there anyway to add 1920x1200 as an option?

Have you installed the drivers for your graphics card? Also, from personal experience, I prefer to use Nvidia's control panel over ubuntu's display settings(forgot what it is called)

---

### Post by rifak on 2009-11-02
ahh yes, i forgot the iMac's have an nvidia card. it should detect the correct resolution with the nvidia driver installed.

---

### Post by cascade9 on 2009-11-02
Actually, iMacs come with both nVidia and ATI graphics- 

[http://www.apple.com/imac/specs.html](http://www.apple.com/imac/specs.html)

Yes, I know thats current models, the 24'' iMacs also came with nVidia and ATI, so I would check before you go downloading drivers.

---

### Post by brucem91 on 2009-11-02
> **cascade9 said:**
> Actually, iMacs come with both nVidia and ATI graphics- 

[http://www.apple.com/imac/specs.html](http://www.apple.com/imac/specs.html)

Yes, I know thats current models, the 24'' iMacs also came with nVidia and ATI, so I would check before you go downloading drivers.

Ah yes, but in my experience, I have had really good luck by going to System -> Administration -> Hardware Drivers. Works very easily, and no having to compile(ive had to manually download a driver and compile on a 6 yr old graphics card. Was not fun)

---

### Post by FirstNameRyan on 2009-11-02
Thanks for everyone's help. I updated the drivers and it detected I was using nvidia card and gave me another control panel for display options were it detected 1920x1200.

---

