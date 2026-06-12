---
title: "Ubuntu live CD problems"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by rik224224 on 2008-02-12
When i boot from the ubuntu 7.10  live CD it loads the screen with the options on it. I select the one to run the live CD. Then there is the Ubuntu logo and a loading bar. After it is finished loading, the screen goes blank and my monitor says that there is no signal.  I have run previous versions of the Ubuntu live cd before on the same computer and they have worked fine.  Could it be that it's not working because i recently replaced my crt monitor with a widescreen LCD monitor? does ubuntu support widescreen? Here are my specs:
amd athlon 64 2.2 ghz
1 gig ram
250 gig hard drive
512mb ati radeon x1600 pro PCI express graphics card

---

### Post by themattjon on 2008-02-12
I'm no expert, but it does sound like it's not recognizing your monitor. Try a different one if one is available. I'm pretty sure it supports widescreen, just maybe not your make and/or model.

---

### Post by oedha on 2008-02-12
have you try ot install in safe graphic mode ?

---

### Post by rik224224 on 2008-02-12
I tried running it in safe graphics mode and that didn't work either.
Does that mean I am going to have to use a different monitor to install it? Once it is installed will it work with my widescreen monitor?

---

### Post by oedha on 2008-02-13
if you have one....why not......widescreen can be set up later on....and display adapter too

---

### Post by rik224224 on 2008-02-15
do u know where i could get the display adapter? i will only be able to borrow a monitor for a little while so I will need to get the display adapter quickly. my monitor is Hanns G HW191D. Thanks

---

### Post by jan quark on 2008-02-15
why don't you try the alternate CD installation

it is a text mode installation and solves many graphical problems

[download here]("http://releases.ubuntu.com/gutsy/")

[guide here]("http://users.bigpond.net.au/hermanzone/p3.htm")

---

### Post by uberlube on 2008-02-15
go into extra options (i think by hitting F6) and type in:
```
vga=791 irqpoll
```

that should do the trick

---

### Post by zerhacke on 2008-02-15
It's not a bug, but a feature, but in my case the monitor dies when it first starts up X.  You have to move the mouse and the screen comes back.

---

### Post by rik224224 on 2008-02-15
i was able to install it using the alternate CD in text mode. however after it was done installing and i booted it my monitor said no input. I am going to borrow a monitor from someone and see if it works. what should i do when i am borrowing the monitor that will allow my widescreen monitor to work?

---

