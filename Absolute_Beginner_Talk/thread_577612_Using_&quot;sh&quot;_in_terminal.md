---
title: "Using &quot;sh&quot; in terminal"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by javafiend on 2007-10-16
I am attempting to install nVidia legacy drivers on an older system running edubuntu.  According to the instructions on the nVidia site, I'm supposed to ype "sh NVIDIA-Linux-x86-1.0-9755-pkg1.run" to install the driver.

Now, my question is since I'm using terminal, do I have to type the "sh" before the install file?

Many thanks!

(BTW, I love this forums similar thread feature!)

---

### Post by maybeway36 on 2007-10-16
That will work just fine. You can also try ```
./NVIDIA-Linux-x86-1.0-9755-pkg1.run
```

---

### Post by FuturePilot on 2007-10-16
You need to run
```
sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run
```
But that is not the legacy driver. And you need to have the dev packages installed.

---

### Post by javafiend on 2007-10-16
Uh oh

This is the link I got from nVidia for my GeForce 400MX.  I would appreciate it if someone could provide a link to the appropriate driver if this isn't the one I need.  Also, what dev packages do I need to install?

---

### Post by bodhi.zazen on 2007-10-16
The driver is on the nvidia site : [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

You need to install build-essential and the kernel headers :

```
sudo apt-get install build-essential linux-headers-`uname -r`
```

---

### Post by javafiend on 2007-10-19
Well, I'm still having graphics issues, but not as bad.  It looks like there might be something wrong with the monitor (a CRT).  I did stumble upon posts talking about ENVY so I'll give that a shot since the post was on a similar card to mine.

Thanks for the assists!

---

