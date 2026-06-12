---
title: "Desktop backround turns into a mess after using virtual terminals"
date: 2011-11-01
forum: Apple Hardware Users
---

### Post by HotForLinux on 2011-11-01
I have just installed an Ubuntu **Natty Narwhal **(amd+mac) on **Macbookpro** 3,1 [Oneiric was a nightmare and almost unusable for many sad reasons] 

I have a number of little problems and doubts which I don't know if I should post in different threads because some might be related. 

[LEFT] 1. When I switch to a virtual terminal and turn back to a graphical  terminal, the desktop background and panels look like a mess. Clicking  over the panels restores them but there's no way to restore the background, even if I chose a new one. I am not sure if this happened with the live CD, I don't think so, but I will check it out.
[/LEFT]

2. Switching among different windows with Alt-Tab is extremely slow. It takes between 3 and four seconds to focus the new window. But it is not slow minimizing and unminimizing windows. Although this is done in a sort of two steps fashion which I would prefer to avoid.
Also, when switching among windows, if I keep the ALT key pressed, so that I can skip along the list of open windows, the change from icon to icon is very slow and done in two steps (it stop a moment in the middle).

3. Writing in this web form (as well as in others), to submit a comment is problematic because it is difficult to control the mouse. If I keep changing the position and clicking in different places and fields, the mouse (neither the touch-pad) respond very well, they get sort of stuck and do not toggle between text mode (cursor) or graphic mode (or pointer). I can see the pointer change to a cursor (vertical line) in some areas but not in other areas of the textarea and after a while that can change.
I cannot choose the arial font because it doesn't appear selected, but I can choose other fonts from the list. I can click on the icons of the top row but not on the icons of the bottom row on top of this textarea.

```
lsmod | grep nvi
nvidia               8107272  36
mbp_nvidia_bl          12951  0
```[LEFT]
[/LEFT]
 
4. In the same HD there's  also a vfat partition and the MacOS partition. At the time of installation I established where to mount this vfat partition, so it appears in /etc/fstab and the MacOS (htfs+) is not mentioned there. But nautilus shows the MacOS partition so that it can be mounted with a click and it does not show the vfat partition although it is correctly mounted at boot time.

a) What should one do to make this partition appear in Nautilus as an element in "computer" and in "Places"?
b) Where is he info that makes the system know how and where to mount the MacOS FS if it is not in the fstab file?

* Now that I edit the post again, I can click on the bottom buttons and select Arial, but it changes every time I reload the page.

---

### Post by HotForLinux on 2011-11-03
As regards to point Nr 3, I have seen that what happens is that inside a small area in the central part of the screen the mouse doesn't work, except for movements. And that happens when all the desktop has been disconfigured, as explained in point Nr. 1

---

### Post by HotForLinux on 2011-11-06
-- bump --

---

