---
title: "Gnopernicus"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by HUCC on 2005-12-03
I am a member of a computer club at a small, rural university.  Our club, which consists of avid Windows users, has recently begun using Ubuntu, especially on those computers that we loan and provide to college students who do not own computers.  So far this has worked surprisingly well.  However, one student is blind, requiring us to start the screen reader in the latest version of Ubuntu--which requries that we install gnopernicus.  What is the easiest way for Linux newbies to accomplish this?  Any help is appreciated.

---

### Post by aysiu on 2005-12-03
Open a terminal and type ```
sudo apt-get update
sudo apt-get install gnopernicus
``` To do it graphically, see the second link in my sig and substitute *gnopernicus* for *blender*.

---

### Post by HUCC on 2005-12-03
Got it--everything is working well and we see how to extend your reply to other issues.  Thanks.

---

### Post by eeried on 2006-04-28
Does gnopernicus requires a powerful CPU (mine is PII 450Mhz and less than 200MB?

---

### Post by Henrik on 2006-04-28
When used in magnifier mode, gnopernicus does require a lot of CPU and memory. The screen reader mode is not so bad, as far as I know, but it will probably depend on which speech synth you use (I have a fast machine, so it might be difficult to compare, but when I run gnopernicus with speech the CPU useage is still only around 10-15%). 

I'm hoping to start development of an Xgl-based magnifier that will use the gpu, which should improve that aspect greatly. [https://wiki.ubuntu.com/GoogleSoC2006](https://wiki.ubuntu.com/GoogleSoC2006)

---

