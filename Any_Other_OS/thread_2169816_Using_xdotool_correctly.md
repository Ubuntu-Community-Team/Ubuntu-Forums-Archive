---
title: "Using xdotool correctly"
date: 2013-08-23
forum: Any Other OS
---

### Post by blackout2 on 2013-08-23
Hello all, I am blackout2, as you can see(I entered Blackout, but that's what it gave me, oh well) and I am looking forward to using your site to it's full potential. I would like to ask, as my first post, why xdotool does not "work" at all on my Mac. 
For your information, this is on my laptop, w/ 10.4.11(I know, it's old) I downloaded Xcode, soley so I can use macports, I tried installing apt, from macports, but after an hour and a half of groaning, wishing it would go faster, something went wrong with installing dpkg, but that's a different story. So, I gave up with apt(maybe a different topic) and tried doing xdotool, the installation went without any hitches, after 2 hours, this is what happened when I did a test run. If you need more info, just ask.
$ xdotool key Caps_Lock
Error: Can't open display: (null)
Bus error
I know this isn't a forum for mac, but mac is based off of Unix, and the terminal is the same bash as Ubuntu, as far as I know. I use Linux on my main computer, and am somewhat experienced in it(sort of[probably not{but a little}]).
;D
Thanks ahead of time.

---

### Post by rai_shu2 on 2013-08-23
Hello. Welcome to the forums.

The Mac isn't really good for X11 support (which is what xdotool requires). It's been a few years, but I think if you had an X server running and then pulled up xdotool in a shell from within that, you'd be good to go.

---

### Post by blackout2 on 2013-08-23
How would I set up an X server, I  have never done that before, is there something to download, or a series of terminal commands?

---

### Post by Toz on 2013-08-23
Please do not bump your posts more than once in 24 hours. When people are available, and if they know the answer, they will answer.

Also moving this post to **Other OS/Distro Support**.

---

### Post by blackout2 on 2013-08-23
Np, duly noted, waiting patiently by computer, meanwhile using my Desktop to do it...still need for laptop though.

---

