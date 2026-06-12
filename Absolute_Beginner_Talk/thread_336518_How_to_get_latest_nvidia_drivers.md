---
title: "How to get latest nvidia drivers?"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2007-01-11
Hi all!

After getting my Ubuntu working again the other day I now find that I have Nvidia driver 1.0.8776 but Google Earth is acting VERY WEIRD!  The planet is patchy and bits of each continent are all over the place.  Before I am sure I was using the latest beta drivers, 9xxx and it worked fine with them.  The problem is, I haven't been able to find the post of how to install them. ](*,)   Can anyone help?

Russty.

---

### Post by taurus on 2007-01-11
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by Russty of Oz on 2007-01-11
WOW! that was fast!  

Thanks I will give it a try.

Russty. :D

---

### Post by Russty of Oz on 2007-01-11
OK, I added the repo to my /etc/apt/sources.list and then did sudo aptitude update but I still have the same drivers.

What am I missing?

---

### Post by taurus on 2007-01-11
What version do you have on your computer right now?

---

### Post by Russty of Oz on 2007-01-11
> **taurus said:**
> What version do you have on your computer right now?

1.0.8776

---

### Post by firezip on 2007-01-11
Download Envy

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

-------------------------

1.Press Ctrl + Alt + F1

2.Login to Ubuntu

3. Type sudo envy

4. When the envy menu shows up type "1"(Without quotes) and then press enter.

---

### Post by Russty of Oz on 2007-01-11
Well, I did all that as per the instructions but now I just have the black screen to log into again!  SIGH!:(   I am having to use windows again, what a pain!

So, what has gone wrong?   How do I fix it?

I have to go out now but will be back in a couple of hours, I look forward to seeing how to fix it.

Russty

---

### Post by thewump on 2007-01-11
I had a really hard time with nVidia drivers over the weekend.  In the end I followed the instructions to install the nVidia proprietary drivers.. those were somewhere at [http://www.beryl-project.org/](http://www.beryl-project.org/) which ( for your convenience ) seems to be down right now.

Keith

---

### Post by Russty of Oz on 2007-01-12
I have finally got it working.  Thanks to Keith I went to the Beryl Wiki and found the install instructions for the nvidia drivers.  So now everything is working just fine! :D   

Thanks everyone. 

Russty.

---

### Post by kj1h234lkj1234 on 2007-01-12
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

Fairly straightforward installation.

After that, Ubuntu will automatically notify you if there are ever updates to the nVidia drivers automatically.

---

