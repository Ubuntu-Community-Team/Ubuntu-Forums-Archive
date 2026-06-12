---
title: "Unable to boot Ubuntu 11 in my mac mini"
date: 2011-08-19
forum: Apple Hardware Users
---

### Post by ffelagund on 2011-08-19
Hello,

I tried every I was able to think about. I'm now trying to install Ubuntu with bootcamp. This is what I did.
a) From Lion, I setup bootcamp and allocated a big chunk of disk for Ubuntu.
b) Installed refit
c) Installed Kubuntu (Ubuntu gave me the same results)

Now, in the refit menu, I see a penguin and when I click on it, grub appears. Well, until this point all was correct, but when I press enter in the first grub option, some graphics artifacts appears in the screen and the system doesn`t boot.

I have to say that if I use Ubuntu 8, the system loads correctly (if I can't fix this today, I will go through installing  Ubuntu 8 and perform a dist-upgrade...)

My mac mini is a Core 2 Duo 2.00 GHz, 2 Gb RAM and NV9400 as gfx. 

Any help would be really appreciated, because this is the third day I'm spending with this issue.

Edit: I don't need any kind of graphics for this machine rather than a text console, so if the corruption at init could be skipped forcing text mode, it would do the job perfectly.

---

### Post by linuxopjemac on 2011-08-19
[http://blog.costan.us/2009/03/ubuntu-810-or-904-on-mac-mini.html](http://blog.costan.us/2009/03/ubuntu-810-or-904-on-mac-mini.html)

---

### Post by ffelagund on 2011-08-19
That's the tutorial I'd followed :/

Edit: Fixed by adding nouveau.modeset=0 to the grub line

---

