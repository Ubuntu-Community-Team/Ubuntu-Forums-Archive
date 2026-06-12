---
title: "In this pic, how to clear the background of  &quot;noise&quot; and undo shake"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-04-02
Hello, I'm trying to clear this picture of all noise in the background. For example, the monitor/tv on the upper right may be easy to black out (crop). But the  whitening (overexposure) of the subject's hair is harder to remove. How would you suggest we put back the hair to its original brown color?
Basically, all that I would like to have remaining in this photo is the subject-- his head, and his shoulders and clothes. Everything else, I want to clear. But I find it hard to get a clean "wipe" along the edge between the subject and his background. What do you suggest?

Also, I think the photographer did not have steady enough hands when the shutter went off. Can a photo-editing software (e.g. Gimp) make some magic and remove the "shake" from this picture?

---

### Post by girishv on 2007-04-02
Hi,

this is not going to help you do all the things you want to. That needs patience and takes time. Here, I am going to help you in achieving the desired effect (as close as possible) using GIMP.

1. Blown out details

An easy way to this is to duplicate the photo in layers and multiply or overlay it. Once you are satisfied with the hair, add the layer mask (right click in the layers window on the copy) and using the gradient tool, fill the mask. This is similar to using Graduated neutral density filter.

2. Hand shake

In the thumbnail, I can not say how bad the shake is. You can sharpen the image either using sharpening filter and USM (unsharp mask), and or both. 

The brown color of the hair can be similarly repaired with levels tool.

Girish

---

### Post by Jussi Kukkonen on 2007-04-02
It's not so much a problem of shaky hands, but a lousy camera -- there was obiously not enough light to get a decent picture with the lens that was used (the yellowish hue and the noise all over the image are evidence of that). I bet it was a really tiny lens, maybe a camera phone? Most camera phones just can't take decent pictures indoors.

---

### Post by mahiyar on 2007-04-02
There are a lot of settings available in Picassa, you can try that. I do not remember if it is in the repositories.

---

### Post by Jussi Kukkonen on 2007-04-02
> There are a lot of settings available in Picassa, you can try that. I do not remember if it is in the repositories.
It's not free software, so I don't think you'll find it in the repositories.

---

### Post by deanlinkous on 2007-04-02
bad pic, period....

---

### Post by kittyhawk63 on 2007-04-02
> **Jussi Kukkonen said:**
> It's not free software, so I don't think you'll find it in the repositories.

Picasa is free. I've downloaded it from the Internet for WinxXP and have used it for several years. Picasa is also available through Automatix. You'll find it under Office.  I haven't check it out to see if Picasa for Linux has the same features as Picasa for Windows.

---

### Post by airtonix on 2007-04-02
can you get teh source files of picasa...i think not.

so therefore it is not free.

---

### Post by brennydoogles on 2007-04-02
> **Jussi Kukkonen said:**
> It's not free software, so I don't think you'll find it in the repositories.

Picassa is free software put out by Google, and you can get it by installing Automatix.

---

### Post by hanzj on 2007-04-02
No, the photo was not taken with a camera phone. The flash was turned off so that attention will not be drawn to burst of bright light. The camera automatically chose to have the shutter setting slow down, in order to get more light.

---

### Post by hanzj on 2007-04-02
Thanks, Grishv. I'm not good at using gimp, but I'll try to do what you suggested.

---

### Post by Jussi Kukkonen on 2007-04-03
> **brennydoogles said:**
> Picassa is free software put out by Google, and you can get it by installing Automatix.

Ok, brennydoogles, you are free to express the situation like that. However, I'd like to point out that the term "free software" usually means something quite different in these circles. This is how Ubuntu.com defines it:
[QUOTE=http://www.ubuntu.com/community/ubuntustory/philosophy]For Ubuntu, the 'free' in 'free software' is used primarily in reference to freedom, and not to price - although we are committed to not charging for Ubuntu. The most important thing about Ubuntu is that it confers rights of software freedom on the people who install and use it. It is these freedoms that enable the Ubuntu community to grow, continue to share its collective experience and expertise to improve Ubuntu and make it suitable for use in new countries and new industries.

Quoting the Free Software Foundation's 'What is Free Software', the freedoms at the core of free software are defined as:

    * The freedom to run the programme, for any purpose.
    * The freedom to study how the programme works and adapt it to your needs.
    * The freedom to redistribute copies so you can help others.
    * The freedom to improve the programme and release your improvements to the public, so that everyone benefits.
[/QUOTE]
Just to make the point clearer:
  * You are not allowed to use Picasa for any purpose you want
  * You are not allowed to adapt it to your needs
  * You are not allowed to redistribute Picasa
  * You are not allowed to improve Picasa
So personally I'm not going to call Picasa free software, at least not on a linux forum.

---

