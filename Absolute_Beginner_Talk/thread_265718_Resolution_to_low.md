---
title: "Resolution to low"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by jamesrose on 2006-09-26
Ok, i had a 15" monitor, now ive got a dell 17" that goes much about 1024x768, but the highest default ius 1024, how can i make it go higher?


Thanks.

---

### Post by Josh1 on 2006-09-26
> **jamesrose said:**
> Ok, i had a 15" monitor, now ive got a dell 17" that goes much about 1024x768, but the highest default ius 1024, how can i make it go higher?


Thanks.

Install the drivers for the video card then you can change it to higher then 1024x768 :)

---

### Post by jamesrose on 2006-09-26
I have! 

Got the Nvidia Drivers installed!!!

---

### Post by Bachstelze on 2006-09-26
sudo dpkg-reconfigure xserver-xorg

---

### Post by jamesrose on 2006-09-26
Do i need to restart my pc?

---

### Post by BrianAT on 2006-09-26
I had the same problem.
I fixed it by running
```
sudo dpkg-reconfigure xserver-xorg
```

I did that by booting into safe mode (or whatever it is called, I can't recall now, it was the second option after the default) :D 
Anyhow, when in there, I set things mostly to the defaults, but I did set my monitor up, and somewhere along the line I chose nVidia rather then nv for the driver. The big thing was there was a screen where I could choose resolutions for it to support, and there I added 1280X1024 (the max my monitor can handle). It is fairly self guiding once you get into it.
[This thread]("http://www.ubuntuforums.org/showthread.php?t=83678") has more details, although it is for Breezy Badger (5.10) rather then Dapper Drake (6.06).

Edit: Beat to it by HymnToLife

---

### Post by jamesrose on 2006-09-26
Ahhh. It randomly chooses a dodgy resolution, wont do the one i want!

---

### Post by bulldog on 2006-09-26
> **jamesrose said:**
> Ahhh. It randomly chooses a dodgy resolution, wont do the one i want!

Take a look in your xorg.conf if your desired resolution is there.

cat /etc/X11/xorg.conf

If so set is as your default with an dept of 24.

---

### Post by jamesrose on 2006-09-26
Yay thankyou very much. Your all great here, i can rely on you! Cheers!

Ps. I choose the wrong driver :P

---

