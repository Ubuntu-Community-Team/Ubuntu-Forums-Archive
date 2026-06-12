---
title: "Dell printer"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by ffsct1 on 2008-02-18
I have just installed Gutsy Gibbon and have successfully installed a local printer (an HP). When I tried to install a network printer using the method below, it failed to list the model (Dell 3100cn)
   1. select connection
   2. Select Manufacturer
   3. Select Model
   4. Enter printer info
   5. Enter Password

I went to Dell's site and they list a Linux driver for Suse: Dell-Laser-Printer-3100cn-1.3-1.noarch.rpm

Would this work in Ubuntu? If so how? Also I have heard that CUPS might work, could someone point me to a good tutorial?

Thanks

ffsct1

---

### Post by spiderbatdad on 2008-02-18
cups is installed by default under Administration>>Printing...you can also go directly to cups configuration by entering  localhost:631 in your browser address bar. That's probably your best bet for configuring the printer...otherwise using alien on that driver might work, but is a big ? in my mind...see:[http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/](http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/) for info on alien.

---

### Post by ffsct1 on 2008-02-19
Thanks, I'll try your suggestions!

---

### Post by ffsct1 on 2008-02-23
I finally got  my Dell network printer installed and working in Ubuntu. I used alien to convert the .rpm package to a usable .deb package, it worked flawlessly. I had to do some more research to find out about using fakeroot to get permission to install the package and that also worked well. So now I have a Dell 3100cn printer installed using drivers from Dell's site which were meant to be used with Red Hat Enterprise Linux 4.

---

