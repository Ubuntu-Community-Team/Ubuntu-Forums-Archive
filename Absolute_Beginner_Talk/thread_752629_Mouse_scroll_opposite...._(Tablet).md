---
title: "Mouse scroll opposite.... (Tablet)"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by waggingwabbit on 2008-04-11
guys!!!! hello! my fellow ubuntu-ies! 

i just installed ubuntu and don't know anything about it really...so i got a lot of questions, but I just want to ask one right now. I have a Wacom Intuous3 6x8 Tablet and when I use the mouse on it, I notice that it is slower than it was on XP, and also the wheel scrolling is opposite, when i scroll down, the browser goes up, and vice versa... and I guess middle click is "paste" now? instead of being able to hold down the middle button on firefox to scroll now, it pastes whatever i just copied or cut? Are there ways to change this? I'm on version 7.10. Can someone please help me fix this?

thanks!!!

---

### Post by spiderbatdad on 2008-04-11
Read this report...several workarounds are suggested: [https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/77226/](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/77226/)

QUOTED:
I found a fix (well a work-around). Install wacom-tools, then run the following:

user@host$ xsetwacom get cursor RelWDn
5
user@host$ xsetwacom get cursor RelWUp
4

Here is the the real problem, change them with the following two commands:

user@host$ xsetwacom set cursor RelWUp "5"
user@host$ xsetwacom set cursor RelWDn "4"

---

### Post by waggingwabbit on 2008-04-12
oh...what program do i have to get into inorder to enter those commands?

---

### Post by waggingwabbit on 2008-04-12
can someone teach me how to install wacom tools? i found 2 links:

[https://launchpad.net/ubuntu/gutsy/+source/wine/0.9.58-0ubuntu3~gutsy1](https://launchpad.net/ubuntu/gutsy/+source/wine/0.9.58-0ubuntu3~gutsy1)

this one has 3 download options. i downloaded and extracted them, but i have no idea what to do. do i even need all 3 of them?

the other link is this:
[http://packages.debian.org/testing/utils/wacom-tools](http://packages.debian.org/testing/utils/wacom-tools)

i have an amd64, but when I choose that option, it says I have the wrong wrong architecture...

---

### Post by Saint Angeles on 2008-04-12
using the 3rd button for pasting is an awesome feature of linux... also, selected text is automatically copied to the clipboard.

ctrl+c and ctrl+v are so 1990s

EDIT: i just realized that firefox has an option for "use autoscrolling" i don't use it but i think its what you're looking for.

---

### Post by waggingwabbit on 2008-04-12
> **Saint Angeles said:**
> using the 3rd button for pasting is an awesome feature of linux... also, selected text is automatically copied to the clipboard.

ctrl+c and ctrl+v are so 1990s

EDIT: i just realized that firefox has an option for "use autoscrolling" i don't use it but i think its what you're looking for.

yes it was! =D 

thanks for that, and the info about the auto copying.

---

### Post by waggingwabbit on 2008-04-12
> **spiderbatdad said:**
> Read this report...several workarounds are suggested: [https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/77226/](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/77226/)

QUOTED:
I found a fix (well a work-around). Install wacom-tools, then run the following:

user@host$ xsetwacom get cursor RelWDn
5
user@host$ xsetwacom get cursor RelWUp
4

Here is the the real problem, change them with the following two commands:

user@host$ xsetwacom set cursor RelWUp "5"
user@host$ xsetwacom set cursor RelWDn "4"

can you tell me where to change the 4 5 from the link you provided? I just figured out how to install wacom-tools and edit xorg.conf. i did the things it said to do here: [http://ubuntuforums.org/showthread.php?t=25151&highlight=wacom](http://ubuntuforums.org/showthread.php?t=25151&highlight=wacom)
but the opposite wheel thing is in a different file I'm thinking...I don't know which one it is or how to get to it....

---

### Post by spiderbatdad on 2008-04-12
> **waggingwabbit said:**
> can you tell me where to change the 4 5 from the link you provided? I just figured out how to install wacom-tools and edit xorg.conf. i did the things it said to do here: [http://ubuntuforums.org/showthread.php?t=25151&highlight=wacom](http://ubuntuforums.org/showthread.php?t=25151&highlight=wacom)
but the opposite wheel thing is in a different file I'm thinking...I don't know which one it is or how to get to it....

Just run the two commands from a terminal window, Applications>>Accessories>>Terminal...is what I gathered from reading the report: Open Terminal enter each line separately:

```
xsetwacom set cursor RelWUp "5"
xsetwacom set cursor RelWDn "4"
```

---

### Post by Under_score on 2008-06-29
Hi,

I've got an acer aspire 5315, and I've got the latest version of ubuntu, I also seem to have the same problem as you guys, which is my middle scroll button works the wrong way, ie it scrolls up when I press down and down when I press up, I tried the above suggestions and they didn't work so can some help me?  :confused:

---

