---
title: "X Plane Demo Installation (linux distro)"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by SavageFreedom on 2007-01-15
Problem solved. I had to set the file's permissions for it to be run as an executable.

I downloaded the X-Plane Demo Net installer from teh x-plane.com ... It gave me a .gz file, which I used gunzip to decompress. That gave me an 11.5mb executable, but every time I try to run it, ubuntu tells me that there is no program set to handle files of that type. There is no file extension, so I don't know what to do.

---

### Post by crispy_420 on 2007-01-15
Did you set it as executable? If so then go to whatever directory you downloaded to.

> cd /home/X-Plane (or where ever you picked)
./X-Plane-Net-Install

Don't think you need sudo here, I didn't complete install. But if so just issue this command instead:

>  sudo ./X-Plane-Net-Install

---

