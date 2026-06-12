---
title: "Screen Resolution"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by rammstein2133 on 2007-09-30
I recently installed Ubuntu in dual-boot with Vista and got it to a state in which I was more than happy to continue using it over Vista with 1280x800 resolution. But I wasn't able to correctly install my video card drivers so I was just using the Vesa driver. We went back and tried re-installing Ubuntu to see if the drivers would install correctly then. They didn't. I have come to accept that the drivers will not work, but ever since we re-installed Ubuntu, the screen resolution will only go to 1024x768 even after selecting 1280x800 during install. I know my usage of Ubuntu shouldn't depend on a small difference in resolution, but it just bugs the crap out of me to see everything stretched out and so unclear. Anyone able to help me?

---

### Post by kellemes on 2007-09-30
Please give us a little info about the hardware you're using, I can't help you install a driver if I don't know what videocard you have..
And reinstalling Ubuntu is never gonna give you the preferred driver for your videocard, this is the same thing with Windows. Drivers need to be installed after system-install.

---

### Post by rammstein2133 on 2007-09-30
I already made a thread about installing the drivers post-install and all the advice I received did not work. I have an nVidia 8600M GS. I went through manual install multiple times and even used Envy. No results. Every time I started the system up after installing the nVidia drivers, my screen would just go blank and would do nothing. So we'd have to go to the backup settings.

---

### Post by kellemes on 2007-09-30
Maybe this thread will help you? It seems this card **can** function.
[http://ubuntuforums.org/showthread.php?t=543019&highlight=8600M+GS]("http://ubuntuforums.org/showthread.php?t=543019&highlight=8600M+GS")

Listen.. installing the preferred driver for your videocard can be horror sometimes.. a couple of years ago it took me 3 weeks to get my card going. ](*,)

---

### Post by rammstein2133 on 2007-09-30
Ok.. I'll have my friend look at that page and see if it's any different from what he's been trying already, but in the meantime, do you know how I can get my correct resolution in Vesa to work?

---

### Post by kellemes on 2007-09-30
> **rammstein2133 said:**
> Ok.. I'll have my friend look at that page and see if it's any different from what he's been trying already, but in the meantime, do you know how I can get my correct resolution in Vesa to work?

VESA is no more then a fallback-driver, it will give you X, nothing fancy and most often not the best resolution for your card, I believe it's maximum resolution is 1024x768.
And so you really need to install the nvidia-driver.

---

### Post by rammstein2133 on 2007-09-30
We had it in 1280x800 before re-installing Ubuntu, but now we can't get it to go back. I guess I'll just deal with what I've got have him look at that thread you gave me when he gets back on campus. Thanks for your help.

---

