---
title: "How do you install Beryl"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by CloudFX on 2008-03-05
I've heard a lot about Beryl, but I'm having trouble installing it. I'm a beginner to Ubuntu, and have little to no knowledge of the terminal. I downloaded the tar file, and I'm lost from there. What shallst I do next? Thanks!:KS

---

### Post by overdrank on 2008-03-05
> **CloudFX said:**
> I've heard a lot about Beryl, but I'm having trouble installing it. I'm a beginner to Ubuntu, and have little to no knowledge of the terminal. I downloaded the tar file, and I'm lost from there. What shallst I do next? Thanks!:KS

HI and if you are using gutsy you could try compiz fusion as beryl has merged with compiz. 
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

### Post by CloudFX on 2008-03-05
Thanks, I just discovered that myself. The problem is, when I try to enable visual effects, it says "The composite extension is not available".

---

### Post by overdrank on 2008-03-05
> **CloudFX said:**
> Thanks, I just discovered that myself. The problem is, when I try to enable visual effects, it says "The composite extension is not available".

Ok what is the model of the graphics card and have you installed the drivers for it?

---

### Post by santiagoward2000 on 2008-03-05
> **CloudFX said:**
> Thanks, I just discovered that myself. The problem is, when I try to enable visual effects, it says "The composite extension is not available".

Hi!
What video card do you have?

---

### Post by Fixman on 2008-03-05
> **santiagoward2000 said:**
> Hi!
What video card do you have?

To know that, you can go to applications->accesories->terminal, and there write

```
 
lspci | grep VGA

```

And post the results.

---

### Post by overdrank on 2008-03-05
> **CloudFX said:**
> Thanks, I just discovered that myself. The problem is, when I try to enable visual effects, it says "The composite extension is not available".

Quote
I too am unable to enable visual effects. I have a Radeon X1270... is this not good enough?
From
[http://ubuntuforums.org/showthread.php?p=4458977#post4458977](http://ubuntuforums.org/showthread.php?p=4458977#post4458977)
You may try Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by CloudFX on 2008-03-06
I have now enabled visual effects with the help from another thread! Thanks to all.

---

