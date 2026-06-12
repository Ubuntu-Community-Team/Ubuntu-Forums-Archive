---
title: "Webcame problem"
date: 2011-06-17
forum: Asus Ubuntu Support (CLOSED)
---

### Post by whynot on 2011-06-17
Hi
i have an Asus F9F Laptop with ubuntu 11 installed. How could we run or start webcame that integrated in this laptop.

```

Bus 001 Device 002: ID 174f:6a31 Syntek Web Cam - Asus A8J, F3S, F5R, VX2S, V1S

```
but there is no file called /dev/video*

Here are some outputs 
```

$ lsmod |grep -i video
video                  18951  1 i915
(i installed v4l-conf from apt-get depot)
$ v4l-conf
v4l-conf: using X11 display :0
dga: version 2.0
WARNING: No DGA direct video mode for this display.
mode: 1280x800, depth=24, bpp=32, bpl=5120, base=unknown
can't open /dev/video0: No such file or directory

```


Thanks.

---

### Post by whynot on 2011-06-20
> **whynot said:**
> Hi
i have an Asus F9F Laptop with ubuntu 11 installed. How could we run or start webcame that integrated in this laptop.

```

Bus 001 Device 002: ID 174f:6a31 Syntek Web Cam - Asus A8J, F3S, F5R, VX2S, V1S

```
but there is no file called /dev/video*

Here are some outputs 
```

$ lsmod |grep -i video
video                  18951  1 i915
(i installed v4l-conf from apt-get depot)
$ v4l-conf
v4l-conf: using X11 display :0
dga: version 2.0
WARNING: No DGA direct video mode for this display.
mode: 1280x800, depth=24, bpp=32, bpl=5120, base=unknown
can't open /dev/video0: No such file or directory

```


Thanks.

Please guys i need help??

---

### Post by nshensfeek on 2011-06-23
Hi buddy i'm not sure there's a v4l2 option.Try it out.
I've also got the same problem i'll get back soon after tryin' it out.

---

### Post by nshensfeek on 2011-06-23
Hey i got it working now.

Now try this
1)Open terminal
2)Type "gstreamer-properties" without quotes and go for the video tab and checkout whether your webcam is working or not.
3)Try updating all your v4l and v4l2 files in your repo i think it's there by default.

After this reply me whether its working or not

---

### Post by whynot on 2011-07-04
> **nshensfeek said:**
> Hey i got it working now.

Now try this
1)Open terminal
2)Type "gstreamer-properties" without quotes and go for the video tab and checkout whether your webcam is working or not.
3)Try updating all your v4l and v4l2 files in your repo i think it's there by default.

After this reply me whether its working or not

I think there is no device v4l2src.
And under /dev/
there are some files called 
vcs 
vcs1-7(vcs1,vcs2....) 
vcsa 
vcsa1-7 
vga_arbiter
and 
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install v4l*

```
but no changes in gstreamer-properties

---

