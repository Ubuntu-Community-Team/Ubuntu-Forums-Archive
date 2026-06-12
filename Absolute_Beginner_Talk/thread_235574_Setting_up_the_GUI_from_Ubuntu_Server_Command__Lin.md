---
title: "Setting up the GUI from Ubuntu Server Command  Line."
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by martinmanzana on 2006-08-13
I have an old laptop: Toshiba  2250XCDS. It has a Celeron 600Mhz, 64Mb of Ram and 6Gb of HDD. Due to suggestions on prior threads I posted, I installed Ubuntu Server Version. This means I have no GUI at all. I have to do everything from the command line. This becomes stressing since I am completly new to Linux.

You may be asking yourself. Why is this guy, who knows nothing of linux, installing Ubuntu Server on his machine? My idea, or as someone suggested was, to install ubuntu server (since it worked with low ram) and later put a light GUI, such as fluxbox. So far, I got no GUI, but I got this terrible headache.

So as I said, I have ubuntu server installed correctly on my machine. Or that's what I think, since I can log on to the machine perfectly. Now, what I tried to do was, install the X windows system packages. On prior post, someone listed fo me, the packages that I had to install in order to get the x windows system running. I couldn't find the packages that he listed. Instead I found, under the "Not Installed Packages" option, a sub-option titled "x11 - The X window system and related software" I went ahead and installed all of the packages inside this option. On the Blackbox webpage, where it explains how to compile the files to get blackbox working, they listed a couple of programs that had to be installed. I found these packages under the "devel - Utilities and programs form software development" option and I installed them too.

This is as far as I have gotten. I don't know what to do next. Does any have an idea? Can any help me?

Thanks.

---

### Post by Joey French on 2006-08-13
So, are you just trying to install fluxbox? Go to the terminal (bash) and type 
```
sudo apt-get install fluxbox
```
I would guess. It should really be that easy.

---

### Post by martinmanzana on 2006-08-13
When I type this in it shows an error saying it can't find the package fluxbox. I am guessing it shows this since I don't have the packages on my machine. What I do have is the blackbox binaries. But anyway is it posible to run x windows system without a windows manager like fluxbox or blackbos? Or do need the windows manager?

thanks

---

### Post by az on 2006-08-13
You must enable the Universe repository:
[https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

---

### Post by martinmanzana on 2006-08-13
To use repositories don't I need I connection to internet? My laptop has no access to internet. But I got my desktop working with a connection to internet. Can I dowloaded on my desktop, save it on a floppy or a CD, mount it on the laptop and use it? I also have and xubuntu iso burned on a cd. Is that of any use? I got the blackbox binaries allready inside the laptop, I can compile them. Is that too hard? I think I can get the fluxbox binaries into the laptop the same way I got the blackbox ones. But before any of this. How do I get the X window system running? Or is it already enough with what I installed?

Thanks

---

