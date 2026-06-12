---
title: "Macbook ubuntu wiki Sound typo?"
date: 2009-08-25
forum: Apple Hardware Users
---

### Post by dennis123123 on 2009-08-25
I am looking to buy a 13" MBP Unibody soon; I was looking on the Ubuntu wiki for macbook - [https://help.ubuntu.com/community/MacBookPro5-5/Jaunty#Sound](https://help.ubuntu.com/community/MacBookPro5-5/Jaunty#Sound)
and it states kernel version **2.6.32** will support the sound controller without manually compiling.

Is this a typo instead of **2.6.30.2** ??
Looking at [http://www.kernel.org/](http://www.kernel.org/) it seems the latest alpha snapshot is only [B]2.6.31-rc7

[/B]I would just like to know whether it will be ages before native support is introduced for the sound controller, or if its already out in the latest stable kernel!

Also, does anyone know if Apple will release the 5,6 model soon, and will it change (compatibility with linux) much?

---

### Post by amd-64 on 2009-08-25
This is funny. I also saw this comment a few weeks ago when I was considering a MBP. I went a head and got it and after a few hours of going through the forums and wiki, everything was set up with the jaunty kernel 2.6.28. 

You still need to compile the updated alsa modules regardless of the kernel version. It is becoming quite easy now, you won't have to compile a custom kernel and the patch will make its way to a future kernel release, may be 2.6.32 when it is out.

---

### Post by dennis123123 on 2009-08-26
Er... thanks, but that doesn't answer any of my questions!

---

