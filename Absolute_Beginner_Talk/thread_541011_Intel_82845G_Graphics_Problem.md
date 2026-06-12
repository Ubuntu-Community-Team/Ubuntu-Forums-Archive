---
title: "Intel 82845G Graphics Problem"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by GrmRpr3000 on 2007-09-02
Well, after searching, I know that there are a lot of threads on this subject. However, even after reading them I can't get this solved.

I've only been using Ubuntu for a few hours really. I recently acquired an oldish computer, and plan to put in a new hard drive and eventually run it as a basic file server (to stop my brother going "burn more animes plx", and because I can, of course) but before that I need to learn a bit more about Linux and Ubuntu in general. 

The first problem I've come across with that though is screen resolution. The only monitors I have access to have a native resolution of 1680x1050, but so far the max I can get it to display is 1280x1024. This is a problem, as the blurred and stretched look starts to strain the eyes after a while, making it difficult to concentrate on actually learning how to do stuff.

The only solutions I have found for problems similar to this involve using something like 915resolution or whatever it is (I can't remember >.>), and then people saying: wait no, on feisty just use the following command:

```
sudo apt-get install xserver-xorg-video-intel
```

However, using that just gets me this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xserver-xorg-video-intel is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xserver-xorg-video-intel has no installation candidate
```

And now I'm a bit lost about what to do. 

Other than the graphics card (in the title), the only other information I know about is that I'm running Ubuntu 7.04. Beyond that I wouldn't know what information to give you, or how to find it. 

Any help you wonderful people can give would be great. 

Thanks.

---

### Post by GrmRpr3000 on 2007-09-02
Well, just as an excuse to bump this (wow this forum moves fast) I'll post what I've just tried to get it working.

I followed the guides [here](http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/) and [here](http://absolutebeginner.wordpress.com/2006/08/20/absolute-beginner-guide-915resolution/) to try and get it to work, but to no avail. I still can't get it to go above 1280x1024. :(

Maybe I did something wrong, though I'm sure I followed those guides completely. Does anyone else have any advice about what I can do here?

Thanks.

---

