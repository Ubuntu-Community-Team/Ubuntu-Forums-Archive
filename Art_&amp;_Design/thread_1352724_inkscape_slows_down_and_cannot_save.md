---
title: "inkscape slows down and cannot save"
date: 2009-12-11
forum: Art &amp; Design
---

### Post by kangyu29 on 2009-12-11
I only started using it a couple days ago. As soon as I do something, such as resizing a plot, it gets very slow even it ran completely fine and smooth before this action. It gets worse, it stops saving from this point, not to any file formats. In fact, if I try to save it to a existing file, it will ruin the file. I cannot open it again in any programs I have.

I mostly import eps files(exported from mathematica if it matters), and making figures.

Please help!

---

### Post by Exodist on 2009-12-11
Out of curiosity how much CPU & RAM do you have in your system and how did you install Inkscape?

---

### Post by kangyu29 on 2009-12-12
> **Exodist said:**
> Out of curiosity how much CPU & RAM do you have in your system and how did you install Inkscape?

Quad core, 2.8GHz
3Gb Ram

And I installed Inkscape through apt-get.

---

### Post by Exodist on 2009-12-12
> **kangyu29 said:**
> Quad core, 2.8GHz
3Gb Ram

And I installed Inkscape through apt-get.
Hmm..   Which ubuntu version are you running? Sorry forgot to ask that.
Have you checked bug reports to see if anyone else is having this issue. 
It REALLY sounds like a memory leak in Inkscape. You may have to remove it and compile from source.

---

### Post by Ghost|BTFH on 2009-12-12
One thing I can tell you that Inkscape does not like even a little bit, is Compiz.

If you have your visual effects turned on, try turning them off and giving it a go.

Cheers,
Ghost

---

### Post by kangyu29 on 2009-12-13
> **Exodist said:**
> Hmm..   Which ubuntu version are you running? Sorry forgot to ask that.
Have you checked bug reports to see if anyone else is having this issue. 
It REALLY sounds like a memory leak in Inkscape. You may have to remove it and compile from source.

ubuntu 9.10 upgraded from 9.04.

Yes, I have checked, didn't see anything really related. Maybe I will try to compile it.

---

### Post by kangyu29 on 2009-12-13
> **Ghost|BTFH said:**
> One thing I can tell you that Inkscape does not like even a little bit, is Compiz.

If you have your visual effects turned on, try turning them off and giving it a go.

Cheers,
Ghost

Yes, I have tried turn it off. Didn't help. I don't know if this matters, I didn't restart my computer after turn the compiz off.

---

### Post by Exodist on 2009-12-13
> **Ghost|BTFH said:**
> One thing I can tell you that Inkscape does not like even a little bit, is Compiz.

If you have your visual effects turned on, try turning them off and giving it a go.

Cheers,
Ghost
Yea Blender hated my system also running Compiz. This is a good point.


> **kangyu29 said:**
> ubuntu 9.10 upgraded from 9.04.

Yes, I have checked, didn't see anything really related. Maybe I will try to compile it.
May be a mix match of library file from upgrading. Compiling from source should resolve that issue. But I wouldnt guarantee it.

> **kangyu29 said:**
> Yes, I have tried turn it off. Didn't help. I don't know if this matters, I didn't restart my computer after turn the compiz off.
Shouldnt have to restart the PC, just the Xserver. 
What video driver and video card are you running BTW?

---

### Post by kangyu29 on 2009-12-13
> **Exodist said:**
> Yea Blender hated my system also running Compiz. This is a good point.



May be a mix match of library file from upgrading. Compiling from source should resolve that issue. But I wouldnt guarantee it.


Shouldnt have to restart the PC, just the Xserver. 
What video driver and video card are you running BTW?

I don't remember the detail of this video card, it's a computer in my office. I know it is a ATI card.

---

### Post by Exodist on 2009-12-13
> **kangyu29 said:**
> I don't remember the detail of this video card, it's a computer in my office. I know it is a ATI card.
I was wondering if it had anything to do with the Open Source video driver spranging a memory leak or the proprietary driver causing the issue. If you got the open source I highly recommend getting the proprietary driver off of ATI/AMD website. Its much more stable and stops a lot of issues. Most users dont realize there is a better driver and the one that ubuntu downloads for you on to your PC isnt the best.

---

### Post by kangyu29 on 2009-12-13
> **Exodist said:**
> I was wondering if it had anything to do with the Open Source video driver spranging a memory leak or the proprietary driver causing the issue. If you got the open source I highly recommend getting the proprietary driver off of ATI/AMD website. Its much more stable and stops a lot of issues. Most users dont realize there is a better driver and the one that ubuntu downloads for you on to your PC isnt the best.

I am pretty sure I used proprietary driver if it means the same as "restricted driver".

---

### Post by Exodist on 2009-12-14
> **kangyu29 said:**
> I am pretty sure I used proprietary driver if it means the same as "restricted driver".
Actualy NO..  The one that Ubuntu downloads is full of BUGS. Need to go to AMDs website and pick up the newest 9.11(I believe) catylist drivers and install them. That will fix a large handfull of issues.  I have a RadeonHD 4850 in my system. So I have seen how the drivers are. Hope this helps.

---

### Post by kangyu29 on 2009-12-14
> **Exodist said:**
> Actualy NO..  The one that Ubuntu downloads is full of BUGS. Need to go to AMDs website and pick up the newest 9.11(I believe) catylist drivers and install them. That will fix a large handfull of issues.  I have a RadeonHD 4850 in my system. So I have seen how the drivers are. Hope this helps.

I am sorry, now I remember. I did downloaded it from ati.amd.com website and installed myself.(ati hd 3450 binary driver)

I have been working in inkscape today. It works fine, the "workaround" is: 
- I open a empty file, save it in inkscape svg.
- then import my eps files.
In this way, things are working well, I can edit, save etc. without crashing inkscape.

I am not sure what this is, but thanks for all your help.

---

### Post by Exodist on 2009-12-14
> **kangyu29 said:**
> I am sorry, now I remember. I did downloaded it from ati.amd.com website and installed myself.(ati hd 3450 binary driver)

I have been working in inkscape today. It works fine, the "workaround" is: 
- I open a empty file, save it in inkscape svg.
- then import my eps files.
In this way, things are working well, I can edit, save etc. without crashing inkscape.

I am not sure what this is, but thanks for all your help.
That is for sure a Inkscape bug. If you can please take the time to file a bug report out on Inkscapes website. [http://www.inkscape.org/report_bugs.php?lang=en](http://www.inkscape.org/report_bugs.php?lang=en)

Glad to here you have a work around for it. Please include what you had to do to get it to work also.

---

### Post by kangyu29 on 2009-12-14
> **Exodist said:**
> That is for sure a Inkscape bug. If you can please take the time to file a bug report out on Inkscapes website. [http://www.inkscape.org/report_bugs.php?lang=en](http://www.inkscape.org/report_bugs.php?lang=en)

Glad to here you have a work around for it. Please include what you had to do to get it to work also.

Just did it:[https://bugs.launchpad.net/inkscape/+bug/496831](https://bugs.launchpad.net/inkscape/+bug/496831)

---

