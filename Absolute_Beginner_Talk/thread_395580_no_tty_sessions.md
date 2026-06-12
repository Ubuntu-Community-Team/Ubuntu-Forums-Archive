---
title: "no tty sessions"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2007-03-28
For quite awhile I have not had any ctrl+alt+f1,2,3,4 sessions

when I do try to pull up a console the screen just goes black, I am able ctrl+alt+f7 back into x

I have checked and they are being spawned correctly 

It is my feeling that it has something to do with resolution in console view, my lappy's x is set at 1280x800

Does anyone know how to step the res. down when I enter a console session???

---

### Post by charles.g.moore on 2007-03-28
I see others are having this problem but no fixes...

---

### Post by charles.g.moore on 2007-03-28
Alright I have found out that if I change the driver from nvidia to nv in my xorg I get my console back.

Is there an update for the nvidia driver?

Can I have write a script that executes a change in my xorg.conf changing the driver before it tries to start up the tty session.

---

### Post by Grayscale on 2007-03-28
Hi, Could you please share that script?

---

### Post by charles.g.moore on 2007-03-28
> **Grayscale said:**
> Hi, Could you please share that script?

I wish I could, I was actually asking if it is even possible to do.  I dont think so though because the X change required a restart and not just a ctrl+alt+backspace

---

### Post by tseliot on 2007-03-28
Try point 13 of the Problems Section of my guide:
[http://www.albertomilone.com/latest_nvidia_udsf_edgy.html#PROBLEMS_SECTION](http://www.albertomilone.com/latest_nvidia_udsf_edgy.html#PROBLEMS_SECTION)

you can also try leaving "splash" and putting "vga=791" beside it

---

### Post by charles.g.moore on 2007-03-29
> **tseliot said:**
> Try point 13 of the Problems Section of my guide:
[http://www.albertomilone.com/latest_nvidia_udsf_edgy.html#PROBLEMS_SECTION](http://www.albertomilone.com/latest_nvidia_udsf_edgy.html#PROBLEMS_SECTION)

you can also try leaving "splash" and putting "vga=791" beside it

tseliot,
I did point 13 and it worked perfectly!!!  Thank you so much.
All I had to do was remove the 'splash', the vga=791 was in the line above it...

If you have a moment could you tell me why all of the lines are commented out in menu.lst?
I was always under the impression that a commented out line was not 'read' by the OS.
Also, what did the splash screen have to do with my seeing the terminals or not?

---

