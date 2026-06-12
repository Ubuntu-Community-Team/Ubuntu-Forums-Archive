---
title: "How To: New Video Card"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by tordan on 2007-02-14
I just picked up a NVIDIA Model: P55 video card and would love to switch it out for the Radeon 7000 series  that is in my machine and Linux apparently hates. I tried just popping it in and turning on the machine  and it gave me an error and a weird screen and wouldn't let me access the OS. It put me back to a black screen with my normal terminal prompt.
What do I need to do to make this switch happen?

---

### Post by taurus on 2007-02-14
Log in to a console and run

```
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by tordan on 2007-02-14
When I get to the first menu and it asks which card type to configure, I don't know which one to pick. Do you know or should I research it on a certain website?

---

### Post by taurus on 2007-02-14
If you're not sure, just use the default value and pick **vesa** as a driver.  Once you get X running again, then you can install nVidia driver for your card.  Otherwise, you see if from the output of this command.

```
lspci
```

---

### Post by tordan on 2007-02-14
Thanks! You are the shisn.

Got it working with the vesa driver but the svideo output is inoperable. Any suggestions on how to enable it?

---

### Post by taurus on 2007-02-14
Maybe this guide helps.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by tordan on 2007-02-15
Thanks. Alberto was very helpful. I now have the proper driver installed, I believe, but the signal is not getting to the TV. It isn't giving me the option where it seems like it should in the Nvidia setting application.

---

### Post by tordan on 2007-02-15
Does anybody know what this is about?

---

### Post by dcstar on 2007-02-15
> **tordan said:**
> Does anybody know what this is about?

Do a forum search for your video card/problem and see if there are any posts with the solution.

Most of these things have being experienced previously, if you try to dig out the answers yourself it may be a lot quicker than waiting.

---

