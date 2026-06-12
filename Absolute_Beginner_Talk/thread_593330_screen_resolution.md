---
title: "screen resolution"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by ubunt22rock on 2007-10-27
hey i have an acer TM3282
i installed ubuntu7.10

my screnn res is 1280X1024

but my ubuntu doesn show that option
 its runnin on 1024X768

my graphics card is ATI mobility radeon x1400

---

### Post by mikewhatever on 2007-10-27
Have you enabled the restricted ATI driver yet?

---

### Post by alienexplorers on 2007-10-27
You will probably have to install restricted drivers before you can get the screen res you want.

---

### Post by ubunt22rock on 2007-10-28
no i ve not installed restricted drivers yet

can anyone pls guide me how to do it

---

### Post by NedClocker on 2007-10-28
What are restricted drivers?  Why aren't they already installed?

---

### Post by Six_Digits on 2007-10-28
Assuming your on Feisty, first get this to install your video drivers - [Envy]("http://albertomilone.com/nvidia_scripts1.html")

Then try this: 

sudo dpkg-reconfigure xserver-xorg

Most of the time just press OK and choose the options that makes sense. Any questions, ask.

---

### Post by mikewhatever on 2007-10-28
> **ubunt22rock said:**
> no i ve not installed restricted drivers yet

can anyone pls guide me how to do it

System>Admin>Restricted Drivers Manager.

> What are restricted drivers? Why aren't they already installed?

[http://www.michaellarabel.com/?k=blog&i=114](http://www.michaellarabel.com/?k=blog&i=114)
[http://www.google.co.il/search?q=ubuntu+restricted+drivers&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.il/search?q=ubuntu+restricted+drivers&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by ubunt22rock on 2007-10-28
Thanks mikewhatever

its working!!!:)

---

