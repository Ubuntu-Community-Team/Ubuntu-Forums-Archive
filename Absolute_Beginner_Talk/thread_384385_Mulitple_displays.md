---
title: "Mulitple displays"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by joellovr on 2007-03-14
Hello, I am going to install Ubuntu and would like to use my 52 inch hd tv as a second monitor.  I have done this with windows 2000.  I have the nvidia geforce 6600 video card.  What do I have to do.  I want the tv as a second display could even be the clone but would prefer it not to.  What do I have to watch out for?  Any suggestions or help would be greatly appreicated.

Thanks, Joel

---

### Post by omockler on 2007-03-14
I have been running twin view on my Geforce 4000 just fine as a cloned monitor.  To get it to work correctly I had to manually edit the /etc/X11/xorg.config file after setting up that NVidia drivers. I have never tried to have two separate screens, but I have read that it is more difficult.

I also found the drivers on the NVidia website to be a lot better than the ones in synaptic.  You can get them here: [http://www.nvidia.com/object/unix.html]("http://www.nvidia.com/object/unix.html")

Also you might want to look at these pages to get some help with the config file:
[http://www.linuxhardware.org/article.pl?sid=01/05/29/2147241&mode=thread]("http://www.linuxhardware.org/article.pl?sid=01/05/29/2147241&mode=thread") or
[http://mysite.verizon.net/kraussa/nvidia_linux_tv_out.html]("http://mysite.verizon.net/kraussa/nvidia_linux_tv_out.html")

You can also google "nvidia tv out linux" to get a lot of information.

---

### Post by bapoumba on 2007-03-14
Moved to "Absolute Beginner Talk" support forum.

---

### Post by undertherift on 2007-03-14
There is an excellent tutorial written by Zion, at this link.  It worked for me on Nvidia 6600 using twinview. His tutorial points to different tutorials based on what you want to do, as well.


[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

Good Luck!

---

### Post by joellovr on 2007-03-14
thank you

---

