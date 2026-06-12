---
title: "How to remove &quot;damaged&quot; debian package?"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by Andrew Panin on 2006-09-25
Hello!

Here's the problem. I've tried to install the ltmodem-2.6.8-2-386_8.31a11_i386.deb for my laptop's built-in modem. I started it with "dpkg -i ..." in the console. But the installation process failed due to absence of somewhich another package.

And now I can neither remove it (with "dpkg --purge ...") nor install somewhat else using synaptic! That's what I get every time the Synaptic trying to remove the package: "E: ltmodem-2.6.8-2-386: subprocess post-removal script returned error exit status 1".

And when I try to "--purge" it, I get the message that I've not installed the package!

I don't understand anything. What happened?

Please, help! Thanks before!

---

### Post by dmizer on 2006-09-26
you can't remove ltmodem-2.6.8-2-386_8.31a11_i386.deb because the process failed during install.  this means the package never installed, so this package is NOT on your system yet.

figure out the error and why the install process halted. then post that error here.  you'll have to figure out what the absent package is and install it before you can install ltmodem-2.6.8-2-386_8.31a11_i386.deb

---

