---
title: "Ubuntu and Beryl - need advice"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-03-29
I am thinking of trying Beryl with Ubuntu. Just thinking. See my system below in my signature.
Has anyone tried Beryl with Ubuntu using an ATI Radeo 9200Se video card with success?
Thanks for all replies and suggestions.
kh

---

### Post by compmodder26 on 2007-03-29
I had a 9200SE and it ran okay.  A little choppy here and there.  I was running it with the open source radeon xorg driver and aiglx.  Tried it with fglrx and xgl and it kept crashing my computer.

My relevant specs at the time were:

CPU: Athlon XP 2800+
Mem: 512 MB PC 3200 DDR

---

### Post by kittyhawk63 on 2007-03-29
> **compmodder26 said:**
> I had a 9200SE and it ran okay.  A little choppy here and there.  I was running it with the open source radeon xorg driver and aiglx.  Tried it with fglrx and xgl and it kept crashing my computer.
My relevant specs at the time were:
CPU: Athlon XP 2800+
Mem: 512 MB PC 3200 DDR

Thanks for your input. I have only 900mhz. It may be too slow to run Beryl.
kh

---

### Post by spinflick on 2007-03-29
Your 900mhz wont be a problem, I have run it before on 500mhz but on Nvidia.

---

### Post by kittyhawk63 on 2007-03-29
> **spinflick said:**
> Your 900mhz wont be a problem, I have run it before on 500mhz but on Nvidea.

Thanks. Nice to hear this.
kh

---

### Post by kittyhawk63 on 2007-03-29
I'm off to see the eye doctor. Please, don't let that deter you from putting in your $0.2 worth. I can use your suggestions. 

When I return, I will read all posts and will respond to those that have posted if you are asking questions.
Thanks for all the information.
kh

---

### Post by lamalex on 2007-03-29
my advice > just try it. If it doesn't work, uninstall it. Your card can use the better radeon drivers so you won't to deal with fglrx which is the hard part. go for it, if it runs well you'll be glad you did it and if it doesn't you can say "oh well," and move on.

---

### Post by kittyhawk63 on 2007-03-29
> **Iamalex said:**
> my advice > just try it. If it doesn't work, uninstall it. Your card can use the better radeon drivers so you won't to deal with fglrx which is the hard part. go for it, if it runs well you'll be glad you did it and if it doesn't you can say "oh well," and move on.

What "better radeon drivers" are you referring to?
kh

---

### Post by compmodder26 on 2007-03-29
Those are the open source drivers.  You don't need to install anything extra to get them working.  They are installed by default.  To enable them, you just need to change your driver to say "radeon" in xorg.conf under the "Device" section.  For me, I also had to put 

```
Option          "AGPMode"       "8"
Option          "AccelMethod"   "EXA"
Option          "ColorTiling"   "on"
```

in the "Device" section to make it work.

---

### Post by kittyhawk63 on 2007-03-29
Well> **compmodder26 said:**
> Those are the open source drivers.  You don't need to install anything extra to get them working.  They are installed by default.

Well, I didn't know that, but the problem is that the default drivers in Ubuntu do not keep my video from crashing. Every time I do a fresh install, I have had to install fglrx to get the crashes from happening. I wonder if the ATI 8.28.8 driver from ATI.com will improve things. ATI.com says that their 8.28.8 driver supports 3D. Does fglrx support 3D?
kh

---

### Post by compmodder26 on 2007-03-29
I edited my post above with a little more information.  Perhaps that will help you.

---

### Post by kittyhawk63 on 2007-03-29
> **compmodder26 said:**
> I edited my post above with a little more information.  Perhaps that will help you.

  Things are working smoothly right now. I will keep it that way. If I have further problems, I am keeping your information for terminal written down. BTW, do your terminal commands instruct 3D to work?
See next post.
kh

---

### Post by kittyhawk63 on 2007-03-29
> **compmodder26 said:**
> Those are the open source drivers.  You don't need to install anything extra to get them working.  They are installed by default.  To enable them, you just need to change your driver to say "radeon" in xorg.conf under the "Device" section.  For me, I also had to put 

```
Option          "AGPMode"       "8"
Option          "AccelMethod"   "EXA"
Option          "ColorTiling"   "on"
```in the "Device" section to make it work.

How do I get to xorg.conf?

---

### Post by compmodder26 on 2007-03-29
type "sudo gedit /etc/X11/xorg.conf" in a terminal.  Before editing it, you should probably make a backup: "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_back".

---

### Post by kittyhawk63 on 2007-03-29
Thanks.> **compmodder26 said:**
> type "sudo gedit /etc/X11/xorg.conf" in a terminal.  Before editing it, you should probably make a backup: "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_back".

Thanks for the info. One last thing. If I need to go to the "backup" how do I retrieve it?
kh

---

### Post by compmodder26 on 2007-03-29
> **kittyhawk63 said:**
> BTW, do your terminal commands instruct 3D to work?
See next post.
kh

Yes, 3D was fully functional with that setup.

---

### Post by compmodder26 on 2007-03-29
> **kittyhawk63 said:**
> Thanks.

Thanks for the info. One last thing. If I need to go to the "backup" how do I retrieve it?
kh

The command for that would be:

"sudo cp /etc/X11/xorg.conf_back /etc/X11/xorg.conf"

---

### Post by kittyhawk63 on 2007-03-29
> **compmodder26 said:**
> The command for that would be:

"sudo cp /etc/X11/xorg.conf_back /etc/X11/xorg.conf"

Thanks. I will consider this thread closed. Thanks for all your good information and kind assistance.
kh

---

