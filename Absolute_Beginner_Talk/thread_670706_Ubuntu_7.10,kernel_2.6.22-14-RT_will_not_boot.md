---
title: "Ubuntu 7.10,kernel 2.6.22-14-RT will not boot"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Terry N on 2008-01-17
Hello, 
I had Ubuntu 7.10 running on my laptop. Because of my video capture interest I went to the Synaptic package manager and installed everything that was related to Ubuntu Studio. I ended up with two kernels in my grub boot loader, Ubuntu 7.10, kernel 2.6.22-14-RT which when i first tried to boot it it gave me a error of some x system not configured or something like that and now it will go to the Ubuntu boot screen but the progress bar stops about 1/4 of the way and it never boots. The other kernel available is Ubuntu 7.10, kernel 2.6.22.14 generic and it boot fine and boy what a difference in what is available and it is in a Ubuntu Studio environment. Just wondering if I should worry about booting from the other kernel. Are all the same features available in both?

Thanks for all the help,
Terry N

---

### Post by Nerdriot on 2008-02-05
Well, Ubuntu Studio is more geared towards people interested in creating media (which is why it has so many graphic design/audio recording programs installed). If that's not what you're really looking for, chances are, you're not missing much. Especially since, you can download most of the software through Synaptic anyway.

As far as the RT kernel not loading; if you're able to load the Generic, maybe you could remove the RT, and install it again. I'm not really sure why that would happen, but that'd be my first move. If I could see the actual error message, I could probably be more helpful.

---

