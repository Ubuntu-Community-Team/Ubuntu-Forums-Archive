---
title: "Major Slow Down"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by toasty_ghosty on 2008-01-30
Just to start I have used Linux before, mainly Slackware, but wanted to give Ubuntu another shot. I installed it today and began to tweak it to my liking. Everything seemed fine but now after installing XGL and a few other programs and updating everything seems very slow. I dont think I should worry about specs. Heres what I got:

AMD 2.8 ghz Opteron
1 gb of ram (Not much but fast)

Shouldnt this be enough? Or is something running in the background? What about PC Scaling? Any help?

---

### Post by oedha on 2008-01-30
what is you display adapter ?
mine is intel 915 and it will be like yours when i installed xserver-xgl......
now...i dont need that.....and works fine with 3d

~E~

---

### Post by toasty_ghosty on 2008-01-30
I know I should know this, but how would I find that out?

---

### Post by oedha on 2008-01-30
what ?? your display adapter ?
go to system - administration - hardware information
search for VGA
or do you have a manual book of your computer....that will be helped

~E~

---

### Post by Jimmyfj on 2008-01-30
You can find that info when you turn on your computer. Info should be shown on your screen before the BIOS info.

Otherwise you can install either Sysinfo or Hardinfo from Synaptic or Add or Remove programs menu.

---

### Post by asmoore82 on 2008-01-30
Xgl is a major drag.

```
lspci | grep VGA
```
for video card info.

---

### Post by toasty_ghosty on 2008-01-30
Well, I am using a X850XT so I dont think I would be using a VGA adaptor on my motherboard, well actually, I don't have one actually on my motherboard. And if it has to be I just won't use desktop effects..if it helps speed it up.

---

### Post by asmoore82 on 2008-01-30
> **toasty_ghosty said:**
> Well, I am using a X850XT so I dont think I would be using a VGA adaptor on my motherboard, well actually, I don't have one actually on my motherboard. And if it has to be I just won't use desktop effects..if it helps speed it up.

"X850XT" is that ATI?
if so I would suggest using the "Restricted Driver" to get the most out of your hardware,
but keeping Desktop Effects off until an ATI driver that supports them "out-of-the-box" makes
its way into the *buntu Repos, which probably won't be until Ubuntu 8.04 LTS(Hardy Heron).

The newest drivers for Ubuntu downloaded straight from ATI do support desktop effects
but the performance is not up to par with nVidia yet.

P.S. did you run the command anyway? ;) `lspci | grep VGA`

---

### Post by toasty_ghosty on 2008-01-30
I thought that might be it. I am thinking about building myself a new PC soon and I may go with nVidia stuff just for that reason. Heres the print out:

05:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850XT (PCIE)] (Primary)

BTW, thanks. And I just realized something as well. When I shut my PC down it does not shutdown the full shutdown. It makes it to halting all proccesses, shuts down my network connections but stops there. Odd.

---

