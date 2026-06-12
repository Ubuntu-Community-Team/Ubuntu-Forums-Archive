---
title: "mbp-fn-flip a program to swap fn-key functionality"
date: 2012-05-17
forum: Apple Hardware Users
---

### Post by encoded on 2012-05-17
Hi everyone,

I wrote a little program to change the behavior of the Fn-keys on my MacBook Pro. It's a simple program, all it does is write to /sys/module/hid_apple/parameters/fnmode, as described here: [https://help.ubuntu.com/community/MacBookPro6-2/Precise#Keyboard_Functions](https://help.ubuntu.com/community/MacBookPro6-2/Precise#Keyboard_Functions)

The benefit is that it can be installed setuid with owner root, allowing anyone to run it, without having to be root.

Please feel free to check it out and report any issues:

[http://github.com/ewollesen/mbp-fn-flip](http://github.com/ewollesen/mbp-fn-flip)

Thanks!

e.

---

