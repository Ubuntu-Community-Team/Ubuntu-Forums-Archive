---
title: "How to install a driver from a CD"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by eldurso on 2007-10-30
Hi, I am new to ubuntu so please bear with me. Anyways my nvidia graphics drivers are having a lot of errors and I need to install the new ones. I downloaded them from Nvidia's website and I have burned the downloaded file to a cd but I cannot figure out how to install them. I am at a command line style prompt screen and cannot figure out how to change the directory over to my cdrom drive and then install the file on the CD. Any help would be greatly appreciated.

---

### Post by Happy_Man on 2007-10-30
Boot back into your regular Ubuntu (or if you can't, the terminal version), and follow these steps:

If you are in a GUI, open a Terminal with Applications --> Accessories --> Terminal. If you are using a text prompt, log in. 

Now enter this command: ```
cd /media/cdrom
```

And now this one: ```
./<name-of-file>
```

For example, if the file was named "nvidia-gfx-driver.bin", I would enter ```
cd /media/cdrom
./nvidia-gfx-driver.bin
```

---

