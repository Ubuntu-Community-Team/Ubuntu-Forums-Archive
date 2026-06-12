---
title: "Compile new kernel for ibook g3 no have problems"
date: 2008-05-27
forum: Apple Hardware Users
---

### Post by TCE on 2008-05-27
I have a problem i compiled a new kernel for my ibook g3, and even mad sure i included zd1211rw as one of the modules. But when i boot into the new kernel and after i modprobe zd1211rw, i try to sudo ifconfig eth1 up.  Then i get some sort of error like file not found.

---

### Post by stream303 on 2008-05-27
Did you follow the guide here:
[https://wiki.ubuntu.com/PowerPCFAQ#head-faa36f4765cc2dec98f5d029183807b8ccd9a954](https://wiki.ubuntu.com/PowerPCFAQ#head-faa36f4765cc2dec98f5d029183807b8ccd9a954)

Although I guess one has the option of leaving out the low-latency part if that isn't desired...

I'm actually thinking of trying it - when I read the changelogs at kernel.org of all the ppc fixes, I get a bit anxious. :)

**UPDATE:**  it has been awhile since I compiled my own kernel, so I tried this and it works great.  I'm now running 2.6.25.4 generic from kernel.org.

The only thing I had to do with Hardy was in addition to the build-essential development tools and others listed, I had to add *kernel-package* to get it to work.  I also just rebooted after installing the debs without having to use the optional yaboot editing.  I made sure that I could boot back into the old kernel just by specifying "old" at the second-stage yaboot prompt.  Whew, it worked.

This actually fixed a problem I was having with powernowd, where I had to resort to using cpudyn, but with the new kernel, powernowd works like it should.  Dmesg shows that apparmor isn't being loaded, but for a first try with a self-compiled kernel in about 3 years, not so bad. :)  I did change the kernel latency to one designed for the desktop, as it comes default to server, and maybe later I'll recompile again for low-latency.  Not sure if I brought along iptables.

So far, so good.  Once again the Ubuntu community and wiki writers just rock!

---

### Post by TCE on 2008-05-28
oops! Title should say Compiled new kernel for ibook g3 now have problems with wireless.  A little too long maybe. I did follow the guide on powerpcfaq, and works perfect except for wireless. I am glad it worked well for you stream.  I am very impressed with it too, and that is why I am really wishing the wireless would work.  Without wireless my computer is pretty much useless.  Having an airport card would make my life probably a lot easier.

---

### Post by stream303 on 2008-05-29
Wish I knew more, but I'm clueless when it comes to wireless.  I found out I forgot to add iptable support when I wanted to play with the firewall.

I went back to the old oem kernel, since I was just playing around.

---

