---
title: "PC-BSD in Virtualbox"
date: 2007-12-19
forum: BSD
---

### Post by p_quarles on 2007-12-19
Not really sure whether to post this here or in Virtualization, but if I got it wrong it can always be moved. :)

So, I've been trying to setup PC-BSD in Virtualbox, and simply can't get it to boot. The MD5 on the installation image checks out, and the installation itself goes fine. But, when I try to boot from the virtual hard drive, it hangs at the splashscreen. 

I've tried various options from the initial boot menu, but only the command prompt option works. All of the others hang, and rebooting from the command prompt hangs as well. 

I chose to try out this distro because people say it's the "easy" one. I know that with some BSDs, it's necessary to configure Xorg before it will work correctly, but I was under the impression that wouldn't be necessary here. 

Anyway, I'm curious to try this out, so any recommendations about how to get this up and running will be appreciated.

---

### Post by mips on 2007-12-20
Not all guest OSes work in Vitualbox and PC-BSD is one of them right now.
[http://www.virtualbox.org/wiki/Guest_OSes](http://www.virtualbox.org/wiki/Guest_OSes)

For now you might want to try installing to a new partition or maybe try vmware to see if it works with it.

---

### Post by p_quarles on 2007-12-20
Got it. Thanks for the link.

VMware will definitely work, since PC-BSD distributes an image specifically for it. I'll give that a try.

---

