---
title: "Next step: Beryl"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by azkehmm on 2006-12-08
Ok, so, after spending a month or so, getting familiar with the basics in ubuntu, I figured it was time to take the next step and get some sweets for my visual sensors, so I tried to stuff Beryl into my machine.

 Like I expected, after reading a bunch of guides, it didn't turn out to be as easy as, say, scratching my nuts, so after fiddeling with graphics setting and stuff, I find my self in need of a little help.

 I've followed the steps in [url=http://www.ubuntuforums.org/showthread.php?t=290841&highlight=Beryl+Ati]guide, except that my AGP mode is 2 instead of 4, since 4 will make my screen go all black. Now, when I write "beryl-manager" in the terminal, I get this:
```

XGL absent, checking for NVIDIA
Nvidia absent, assuming AIGLX

```
and then gnome freezes and all I can do is ctrl+alt+backspace out and try again. Can someone either assist me with this, or point me in the direction of a troubleshooter?
Thanks in advance.

---

### Post by Adramelech on 2006-12-08
I dont have an ATI video card but i helped a friend with one to install beryl, i remember not all ATI video card can use AIGLX, cause of driver issues, so if your video card is new you have to go with XGL and beryl, i think the newer cards supported are the ones using chip r300.

EDIT: [Supported video cards]("http://gentoo-wiki.com/HOWTO_AIGLX#Cards_Supported")

---

