---
title: "Gimp view gets messed up"
date: 2012-03-21
forum: Art &amp; Design
---

### Post by thorbs on 2012-03-21
I am trying to work with Gimp and some bug (i think) keeps happening. The buttons for enlarging or removing the different gimp windows disapeer.Also it freezes so I can not move the different windows around or resize them. 
The only solution I have been able to restart my computer, but it is every 15 minutes now it is happening. 

Is this a known bug or am I doing anything wrong?

---

### Post by SeijiSensei on 2012-03-21
How much memory does your computer have?  Do you have a swap partition or swap file?  Trying to open large images on a memory-starved machine can cause symptoms like the ones you're describing.

---

### Post by ofnuts on 2012-03-21
> **thorbs said:**
> I am trying to work with Gimp and some bug (i think) keeps happening. The buttons for enlarging or removing the different gimp windows disapeer.Also it freezes so I can not move the different windows around or resize them. 
The only solution I have been able to restart my computer, but it is every 15 minutes now it is happening. 

Is this a known bug or am I doing anything wrong?>What version of Gimp are you running? What is your windows manager? I'm on 10.04 and have no problems with the 2.6.8 from the repository not with a 2.7.2 I compiled a while ago.

---

### Post by thorbs on 2012-03-22
I am actually a bit low on ram, I am thinking of updating anyway. 

I am using the gimp 2.6.1 maybe I should update it as well.

---

### Post by ofnuts on 2012-03-22
> **thorbs said:**
> I am actually a bit low on ram, I am thinking of updating anyway. 

I am using the gimp 2.6.1 maybe I should update it as well.You should mostly take the one from the repository (2.6.8), because it has been tested with the rest of your distro. I wonder how you came to install something older that what your distro comes with...

---

### Post by SeijiSensei on 2012-03-22
Try opening a few small images (< 100K) in the GIMP and see whether you experience the same problems.  If not, it's almost certainly a memory issue.

Remember that the GIMP has to copy the entire image into memory in order for you to edit it and usually needs to make a second copy of the image in order to redraw it with any changes you make.

---

