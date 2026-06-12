---
title: "Failed to start xserver"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by koryo88 on 2006-11-14
I've been using Ubuntu Edgy just fine and I decided to move the hard drive from my home pc to the one at work. When I booted up, however, I got "failed to start xserver" and "no screens found."

So I tried sudo dpkg-reconfigure xserver-xorg and went through the steps to configure that(though most of it was guessing on my part) and then did 'startx.' Now when I boot up I get on the monitor "no signal input."

So I have no idea what happened to my GUI or where to go with it from here. Is it not possible to do easy switches from pc to pc without reconfiguring everything?
Anyway, I'm lost and would appreciate any help I can get.

---

### Post by bodhi.zazen on 2006-11-14
In my experience you can not just move a partition or HD between boxes as you describe unless the architecture is identical. I am suprized it booted at all.

At any rate, you can try: ```
sudo dpkg-reconfigure -phigh xserver-xorg
```Which will select the defaults for you.

---

### Post by taurus on 2006-11-14
When you remove a harddrive from one computer and put it in another, you are changing everything so of course, you need to go back and reconfigure your X over again since you have a new video and new monitor unless you put it in an exact identical machine.  you can try to boot from the LiveCD and mount your harddrive where / is.  Then, copy /etc/X11/xorg.conf from the LiveCD to your harddrive and see if X would happen with that!

---

### Post by koryo88 on 2006-11-14
Well...it's really really wierd, but when I had reconfigured the xserver, I did it on a coworkers pc and of course, it still didn't work. I've got it back on my pc and I'm typing from it right now. It's the wierdest thing. Oh well, guess I'll take it.:) 

Thanks for the suggestions!

---

