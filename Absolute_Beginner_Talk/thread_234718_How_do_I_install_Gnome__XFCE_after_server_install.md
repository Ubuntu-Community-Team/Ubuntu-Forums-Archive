---
title: "How do I install Gnome / XFCE after server install?"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by harisund on 2006-08-11
Ok, I now there is going to be a flood of answers that go 'ubuntu-desktop' 

But here's the catch. *I do NOT want ubuntu-desktop* since it loads a ton of stuff that I don't want to have running. Bluetooth utils is just the least of them. 

Just having a look at [http://packages.ubuntu.com/dapper/base/ubuntu-desktop](http://packages.ubuntu.com/dapper/base/ubuntu-desktop) gives me the shivers. 

I just want plain and simple Gnome. As in the gnome that comes when you download it from the actual gnome website, or a CVS check out of Gnome. 

So what are my options? 

1. Since I only have an AMD4 server right now, I am thinking I could install xserver-xorg (and some other package maybe? If so which ones?), and then actually download a Gnome binary/source from the Gnome website and use that 
2. If I want just the XFCE environment (again, PLEASE no "xubuntu-desktop") and I want to compile it from scratch or something what do I do? 
3. Is there a meta package like gnome-desktop or something that will give me just *THE BASIC* gnome? 

Thanks! I am keening on having just want I want. The last time I installed Ubuntu on my computer, I was annoyed at the long list of processes that run 

cups - I don't have a printer
hplipd - I DONT HAVE A PRINTER
anacron - I will switch this on when I want to
apmd - nope, I use acpi thank you
cron - I dont even want anacron .. 
blah blah and so on. I know, I know, I can stop them all, and prevent them from starting, but the point is can Ubuntu offer me the convenience of Debian/Ubuntu and the power of customization and choosing what I want as Gentoo?

---

### Post by Jagot on 2006-08-11
Well, you can install the packages gnome or gnome-core.  Read about them here to see what they install:

[http://packages.ubuntu.com/dapper/gnome/gnome](http://packages.ubuntu.com/dapper/gnome/gnome)
[http://packages.ubuntu.com/dapper/gnome/gnome-core](http://packages.ubuntu.com/dapper/gnome/gnome-core)

And then xfce4:

[http://packages.ubuntu.com/dapper/x11/xfce4](http://packages.ubuntu.com/dapper/x11/xfce4)

---

### Post by CREEPING DEATH on 2006-08-12
[URL="https://help.ubuntu.com/community/Installation/LowMemorySystems"]Here
[/URL]

CD

---

### Post by harisund on 2006-08-12
Thanks a bunch guys :D. That's what I was searching for :)

---

