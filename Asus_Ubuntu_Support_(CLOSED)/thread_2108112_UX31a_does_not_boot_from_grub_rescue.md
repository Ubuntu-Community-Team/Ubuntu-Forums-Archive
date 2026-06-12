---
title: "UX31a does not boot from grub rescue"
date: 2013-01-23
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Baumkuchen on 2013-01-23
Hi!
I'm experiencing trouble to boot my new UX31a.  I've installed ubuntu 12.04 (64bit) and it worked fine until I tried to perform a kernel update (which I should not have done). Now, when the computer is switched on, it goes to the grub rescue mode with the following error message:

"error: invalid arch independent ELF magic"

This message also appears when I try to load a module with insmod. I've performed an intensive web search (also in this forum) trying to solve this problem, but with no luck. I've tried to boot from USB, but I get the error "unknown filesystem". Putting an ISO image, or even using unetbootin to create a bootable USB stick leads to the same error message (I've tried different USB sticks with various formats).

Of course I've also tried to follow the howto here:
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

But even though I'm able to find the location of the grub2 modules, when I try to load some of them, I get again the error "error: invalid arch independent ELF magic"

This is a real pain and I'm kind of desperate, after almost a week of trying without any result . Any help would be greatly appreciated! There is no data I worry about, so any solution which allows me to boot any OS would be great!


Additional info:
When I've installed ubuntu, the windows recovery partition was overwritten, so there is no comming back to that.

---

### Post by Baumkuchen on 2013-01-25
After some trial and error with unetbootin, I was finally able to solve the problem. My USB stick was recognized as bootable, when I put Kubuntu on it. So I was able to install Kubuntu and don't have to resolve any kernel problems. As a side note, it seems Kubuntu does not run optimally on the UX32a, and since I'm afraid to go back to Ubuntu, I'll probably switch to Mint. 

So long, ubuntu forums! ):P

---

